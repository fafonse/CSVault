#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Thu Dec  4 16:25:13 2025

@author: aidenmichaelteduits
"""

#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Thu Dec  4 15:47:09 2025

@author: aidenmichaelteduits
"""

import warnings
from sklearn.exceptions import ConvergenceWarning

warnings.filterwarnings("ignore", category=ConvergenceWarning)

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay, roc_curve, auc
from scipy import stats

# -----------------------------------------------------------
# 1. Load data and clean column names
# -----------------------------------------------------------
df = pd.read_csv('/Users/aidenmichaelteduits/Desktop/MATH/data 2.csv')
df.columns = df.columns.str.strip()

# Quick check of data dimensions and column names
print("Dataset shape:", df.shape)
print("Columns:", df.columns.tolist()[:10], "...")  # print first 10 column names as example

# -----------------------------------------------------------
# 2. Class distribution plot
# -----------------------------------------------------------
class_counts = df['Bankrupt?'].value_counts()
total = class_counts.sum()

class_df = class_counts.reset_index()
class_df.columns = ['Bankrupt?', 'count']
class_df['Bankrupt?'] = class_df['Bankrupt?'].astype(str)

plt.figure(figsize=(5, 4))
sns.barplot(
    data=class_df,
    x='Bankrupt?', y='count',
    hue='Bankrupt?', dodge=False,
    palette={'0': 'skyblue', '1': 'salmon'},
    legend=False
)
# Annotate each bar with count and percentage
for i, row in class_df.iterrows():
    v = row['count']
    percent = v / total * 100
    plt.text(i, v + total * 0.01, f"{v} ({percent:.2f}%)", ha='center', fontweight='bold')

plt.xlabel('Bankrupt? (0 = No, 1 = Yes)')
plt.ylabel('Number of Companies')
plt.title('Class Distribution: Bankrupt vs Non-Bankrupt')
plt.tight_layout()
plt.show()

# -----------------------------------------------------------
# 3. Correlations with target
# -----------------------------------------------------------
corr = df.corr(numeric_only=True)['Bankrupt?'].drop('Bankrupt?')  # drop target itself

top5_pos = corr[corr > 0].sort_values(ascending=False).head(5)
top5_neg = corr[corr < 0].sort_values(ascending=True).head(5)

print("Top 5 positively correlated features:\n", top5_pos)
print("Top 5 negatively correlated features:\n", top5_neg)

fig, axes = plt.subplots(1, 2, figsize=(12, 5))

# Positive correlations
axes[0].barh(range(len(top5_pos)), top5_pos.values, color='green')
axes[0].set_yticks(range(len(top5_pos)))
axes[0].set_yticklabels(top5_pos.index)
axes[0].invert_yaxis()
axes[0].set_xlabel('Correlation with Bankrupt=1')
axes[0].set_title('Top 5 Positive Correlations')
for i, v in enumerate(top5_pos.values):
    axes[0].text(v + 0.01, i, f"{v:.3f}", va='center')

# Negative correlations
axes[1].barh(range(len(top5_neg)), top5_neg.values, color='red')
axes[1].set_yticks(range(len(top5_neg)))
axes[1].set_yticklabels(top5_neg.index)
axes[1].invert_yaxis()
axes[1].set_xlabel('Correlation with Bankrupt=1')
axes[1].set_title('Top 5 Negative Correlations')
for i, v in enumerate(top5_neg.values):
    axes[1].text(0, i, f"{v:.3f}", va='center', ha='right', color='white')

plt.tight_layout()
plt.show()

# -----------------------------------------------------------
# 4. Boxplots for key features by bankruptcy status
# -----------------------------------------------------------
plt.figure(figsize=(6, 5))
sns.boxplot(x='Bankrupt?',
            y='ROA(C) before interest and depreciation before interest',
            data=df)
plt.xticks([0, 1], ['Not Bankrupt', 'Bankrupt'])
plt.xlabel('Bankruptcy Status')
plt.ylabel('ROA(C) before interest and depreciation')
plt.title('ROA(C) Distribution by Bankruptcy Status')
plt.tight_layout()
plt.show()

plt.figure(figsize=(6, 5))
sns.boxplot(x='Bankrupt?', y='Operating Gross Margin', data=df)
plt.xticks([0, 1], ['Not Bankrupt', 'Bankrupt'])
plt.xlabel('Bankruptcy Status')
plt.ylabel('Operating Gross Margin')
plt.title('Operating Gross Margin by Bankruptcy Status')
plt.tight_layout()
plt.show()

plt.figure(figsize=(6, 5))
sns.boxplot(x='Bankrupt?', y='Debt ratio %', data=df)
plt.xticks([0, 1], ['Not Bankrupt', 'Bankrupt'])
plt.xlabel('Bankruptcy Status')
plt.ylabel('Debt Ratio (%)')
plt.title('Debt Ratio by Bankruptcy Status')
plt.tight_layout()
plt.show()

plt.figure(figsize=(6, 5))
sns.boxplot(x='Bankrupt?', y='Net Income to Total Assets', data=df)
plt.xticks([0, 1], ['Not Bankrupt', 'Bankrupt'])
plt.xlabel('Bankruptcy Status')
plt.ylabel('Net Income to Total Assets')
plt.title('Net Income/Total Assets by Bankruptcy Status')
plt.tight_layout()
plt.show()

plt.figure(figsize=(6, 5))
sns.boxplot(x='Bankrupt?', y='Current Ratio', data=df)
plt.xticks([0, 1], ['Not Bankrupt', 'Bankrupt'])
plt.xlabel('Bankruptcy Status')
plt.ylabel('Current Ratio')
plt.title('Current Ratio by Bankruptcy Status')
plt.tight_layout()
plt.show()

# -----------------------------------------------------------
# 5. Train/test split + scaling
# -----------------------------------------------------------
X = df.drop('Bankrupt?', axis=1)
y = df['Bankrupt?']

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, stratify=y, random_state=42
)

scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# -----------------------------------------------------------
# 6. Logistic regression models (unweighted vs weighted)
# -----------------------------------------------------------
model_no_weight = LogisticRegression(
    penalty='elasticnet',
    solver='saga',
    l1_ratio=0.5,
    class_weight=None,
    max_iter=20000
)
model_no_weight.fit(X_train_scaled, y_train)

model_weighted = LogisticRegression(
    penalty='elasticnet',
    solver='saga',
    l1_ratio=0.5,
    class_weight='balanced',
    max_iter=20000
)
model_weighted.fit(X_train_scaled, y_train)

# -----------------------------------------------------------
# 7. Metrics and confusion matrix
# -----------------------------------------------------------
def get_metrics(y_true, y_pred):
    cm = confusion_matrix(y_true, y_pred)
    TN, FP, FN, TP = cm.ravel()
    accuracy = (TP + TN) / (TP + TN + FP + FN)
    sensitivity = TP / (TP + FN) if (TP + FN) > 0 else 0  # recall for bankrupt (1)
    specificity = TN / (TN + FP) if (TN + FP) > 0 else 0  # recall for non-bankrupt (0)
    return accuracy, sensitivity, specificity, cm

y_pred_no = model_no_weight.predict(X_test_scaled)
y_pred_wt = model_weighted.predict(X_test_scaled)

acc_no, sens_no, spec_no, cm_no = get_metrics(y_test, y_pred_no)
acc_wt, sens_wt, spec_wt, cm_wt = get_metrics(y_test, y_pred_wt)

print(f"Unweighted model - Accuracy: {acc_no:.3f}, Sensitivity: {sens_no:.3f}, Specificity: {spec_no:.3f}")
print(f"Weighted model   - Accuracy: {acc_wt:.3f}, Sensitivity: {sens_wt:.3f}, Specificity: {spec_wt:.3f}")

# Use weighted model as final
cm_best = cm_wt

plt.figure(figsize=(5, 4))
disp = ConfusionMatrixDisplay(confusion_matrix=cm_best,
                              display_labels=['Not Bankrupt', 'Bankrupt'])
disp.plot(cmap='Blues', values_format='d')
plt.title('Confusion Matrix (Test Set) - Weighted Logistic Model')
plt.tight_layout()
plt.show()

# -----------------------------------------------------------
# 8. ROC curve for weighted model
# -----------------------------------------------------------
y_score_best = model_weighted.predict_proba(X_test_scaled)[:, 1]
fpr, tpr, _ = roc_curve(y_test, y_score_best)
roc_auc = auc(fpr, tpr)

plt.figure(figsize=(6, 5))
plt.plot(fpr, tpr, label=f'ROC curve (AUC = {roc_auc:.2f})')
plt.plot([0, 1], [0, 1], 'k--')
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('ROC Curve - Weighted Logistic Bankruptcy Predictor')
plt.legend(loc='lower right')
plt.tight_layout()
plt.show()

# -----------------------------------------------------------
# 9. CI + hypothesis tests for ROA(C) and Debt Ratio
# -----------------------------------------------------------
bankrupt = df[df['Bankrupt?'] == 1]
non_bankrupt = df[df['Bankrupt?'] == 0]

def ci_and_ttest(feature_name):
    x1 = bankrupt[feature_name].dropna()
    x0 = non_bankrupt[feature_name].dropna()

    n1, n0 = len(x1), len(x0)
    mean1, mean0 = x1.mean(), x0.mean()
    var1, var0 = x1.var(ddof=1), x0.var(ddof=1)

    diff = mean1 - mean0
    se_diff = np.sqrt(var1 / n1 + var0 / n0)

    df_welch = (var1 / n1 + var0 / n0) ** 2 / (
        (var1 ** 2) / ((n1 ** 2) * (n1 - 1)) +
        (var0 ** 2) / ((n0 ** 2) * (n0 - 1))
    )

    t_crit = stats.t.ppf(0.975, df_welch)
    ci_low = diff - t_crit * se_diff
    ci_high = diff + t_crit * se_diff

    t_stat, p_val = stats.ttest_ind(x1, x0, equal_var=False)

    print(f"\nFeature: {feature_name}")
    print(f"Mean (bankrupt):     {mean1:.4f}")
    print(f"Mean (non-bankrupt): {mean0:.4f}")
    print(f"Diff (1 - 0):        {diff:.4f}")
    print(f"95% CI for diff:     [{ci_low:.4f}, {ci_high:.4f}]")
    print(f"t-statistic:         {t_stat:.4f}, p-value: {p_val:.4e}")

# ROA(C)
ci_and_ttest('ROA(C) before interest and depreciation before interest')

# Debt ratio %
ci_and_ttest('Debt ratio %')
