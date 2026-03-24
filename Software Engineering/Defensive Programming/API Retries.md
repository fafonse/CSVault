When you're querying something over the web, you need to do a tricky balance of waiting for your answer and retrying your request if the API doesn't return anything.

## Exponential Retries

A solution to the problem is to use exponential retry times.

Basically double your timeout/retry timer for every consequetive request.