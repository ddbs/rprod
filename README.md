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

### Output check: Force NULL whenever result may have zero length

    # zero-length vector
    if(length(res) == 0) res <- NULL
    
 ### Input check: validate object type and object length
 
 Example, to avoid "condition has length > 1" warnings
 
     is_url <- function (s) {
      if(is.character(s) & length(s) == 1) { ## expect a character object with length = 1
        ifelse(substr(s,1,8) == "https://" | substr(s, 1, 7) == "http://", TRUE, FALSE)
      }
      else {
        FALSE
      }
    }
