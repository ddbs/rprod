# rprod
R in Production


## Use `drop = FALSE` when subsetting

To guarantee that result is of same format as source.

Do: 

    res <- names(df[, num_cols, drop = FALSE])
  
Don't: 

    res <- names(df[, num_cols]


## Force NULL for situations where result may have zero length

    # zero-length vector
    if(length(res) == 0) res <- NULL
