Sometimes, the easiest solution is to just delete the missing data. 
## Rows
One of your first options is to drop rows that have missing data. If there are only a few missing samples, you should still have enough concrete data to make claims about the rest of the sample. However, because [[Missing Data|MNAR and MAR]] are so common you data will have some biases introduced. 
> EX: In the [Titanic dataset](https://www.kaggle.com/datasets/yasserh/titanic-dataset), dropping rows where the age are missing leads to more females being present than before. 

## Columns
You can also drop columns, especially if they are extremely [[Sparsity|sparse]].