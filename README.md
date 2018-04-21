# rprod
R in Production


## when subsetting, always use `drop = FALSE`

Do: 

   col_names <- names(df[, num_cols, drop = FALSE])
  
Don't: 

   col_names <- names(df[, num_cols]


## Always force NULL if result is empty or has zero length

   if(length(num_names) == 0) num_names <- NULL

