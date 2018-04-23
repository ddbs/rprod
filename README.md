# rprod

Notes for R in production.

## Subsetting

### Use brackets instead of `$`

Do:

    
    df[["varname"]]
    
    varname <- "varname"
    df[[varname]]

Don't:

    df$varname
    

### Use `drop = FALSE` when subsetting

To guarantee that result is of same format as source.

Do: 

    res <- df[, num_cols, drop = FALSE]
  
Don't: 

    res <- df[, num_cols]


## Validation

### Force NULL whenever result may have zero length

    # zero-length vector
    if(length(res) == 0) res <- NULL
