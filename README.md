# rprod
R in Production


## When subsetting, always use `drop = FALSE`

To guarantee that result is of same format as source.

Do: 

    res <- names(df[, num_cols, drop = FALSE])
  
Don't: 

    res <- names(df[, num_cols]


## Always force NULL if result is empty or has zero length

To avoid unexpected results.

    if(length(res) == 0) res <- NULL

