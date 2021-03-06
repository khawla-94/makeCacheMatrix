# makeCacheMatrix
Peer graded Assignment: Lexical Scoping

## Put comments here that give an overall description of what your
## functions do

## Write a short comment describing this function

## makeCacheMatrix: This function creates a special "matrix" object that can cache its inverse.
## cacheSolve: This function computes the inverse of the special "matrix" returned by makeCacheMatrix.

makeCacheMatrix <- function(x = matrix()) {
inv <- NULL
set <- function(y) {
x <<- y
inv <<- NULL
}
get <- function() {x}
setInverse <- function(inverse) inv <<- inverse
getInverse <- function() inv
list(set = set, get = get,
setInverse = setInverse,
getInverse = getInverse)
}


## Write a short comment describing this function

cacheSolve <- function(x, ...) {
        ## Return a matrix that is the inverse of 'x'
inv <- x$getInverse()
  if(!is.null(inv)) {
    message("getting cached data")
    return(inv)
  }
  data <- x$get()
  inv <- solve(data, ...)
  x$setInverse(inv)
  inv
}
## Testing my program

source("makeCacheMatrix.R")
> mat <- makeCacheMatrix(matrix(1:4, nrow= 2, ncol= 2))
> mat$get()
     [,1] [,2]
[1,]    1    3
[2,]    2    4
> mat$getInverse()
NULL
> cacheSolve(mat)
     [,1] [,2]
[1,]   -2  1.5
[2,]    1 -0.5
> cacheSolve(mat)
getting cached data
     [,1] [,2]
[1,]   -2  1.5
[2,]    1 -0.5
> mat$getInverse()
     [,1] [,2]
[1,]   -2  1.5
[2,]    1 -0.5
