# programming-assignment
## These functions written in partial fulfillment of Coursera Data Science: R Programming 
## Week 3 Assignment; week beginning May 11, 2020; GitHub user: PamlaM


makeCacheMatrix <- function(x = matrix()) 
{
						## This function creates a special "matrix" object that can cache its inverse

makeCacheMatrix <- function(x = matrix()) {		 ## define the argument with default mode of "matrix"
    inv <- NULL                          			   ## initialize inv as NULL; will hold value of matrix inverse 
    set <- function(y) {                  			  ## define the set function to assign new 
        x <<- y                           				  ## value of matrix in parent environment
        inv <<- NULL                      
    }
    get <- function() x                    

    setinverse <- function(inverse) inv <<- inverse  
    getinverse <- function() inv                     
    list(set = set, get = get, setinverse = setinverse, getinverse = getinverse)   
                                                                                
}


cacheSolve <- function(x, ...) {
       
    inv <- x$getinverse()
    if(!is.null(inv)) {
        message("getting cached data")
        return(inv)
    }
    data <- x$get()
    inv <- solve(data, ...)
    x$setinverse(inv)
    inv
}
