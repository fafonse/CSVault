When `NaN` values should be replaced with the previous data entry.

> [!example] Wikipedia Revisions
> For revision history, we want to track the article length. On days where no revisions were made, we just use the previous revision article length.

## Python Usage
```python
revision_df['Article length'].fillna(method='ffill', inplace=True)
```
- Use the *forward fill* method with `fillna`