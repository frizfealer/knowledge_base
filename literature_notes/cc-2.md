2025-04-12T16:40
# Functions in codes
## Contents
1. Functions should be small
	1. If while statements should be one-line long, probably a function call.
	2. Indent level should not be greater than one or two
2. Function should do one thing
	1. If a function does one thing only, it can be describe as a TO sentence. E.g. to get_itinerary_draft, we ask the openai API to generate the response and return in the correct json format
	2. If a function does only those steps that are one-level below the stated name of the function, then the function is doing one thing.
	3. If a function does only one thing we cannot extract another function from it that is not merely a restatement of its implementation.
	4. If you have many sections within a function, then that function is likely doing more than one thing.
3. One level of abstraction per function
	1. Ideally, we want to have code in the order of level of abstraction. First function the highest level, than the middle level, then the lower level.
4. Switch statement
	1. Avoid using switch statement. Using polymorphism instead. Or using switch statement only in a factory-style method that creates the polymorphism objects
5. Use descriptive name, similar as the naming principle in [[cc-1]]
6. Avoid too many function arguments. From the author, larger than three arguments should be avoid. 
	1. We can group multiple arguments into an object to reduce the number of argument, e.g. point x, point y can be grouped into an object coordinate c
	2. We can make argument as instance variable so that it does not need to be in the function arguments.
	3. variable length list of arguments are consider as one argument if they are used in the same way. E.g. printf(template_str, *vars)
7. Function with one argument has three categories. One is asking a question about that argument. Second is operating on that argument. Third is updating the state of the object.
8. Avoid using flag, because it violates do one thing rule. When there is a flag, we should consider divide this function into two functions.
9. Function should not has side-effect, this makes unexpected changes, and could lead to unneeded temporal coupling.
10. If a function is a query function, e.g. asking thing about an argument, it should not operate on the argument. In other words, a function is asking question category should not be operating on argument category.
11. Prefer exception than returning the error codes
	1. Return the error codes makes the caller of the functions to have a nested structure to check if the functions are all successful.
	2. On the other hand, if using exceptions, we can separate the happy path from the error part clearly.
	3. Since try/catch is ugly, it is better to put the main logic in one function, and have try/catch in another function to call the main-logic function.
	4. Function should do one thing and error-handling is one thing
12. DRY principle: don't repeat yourself
13. Structure programming: every function and every block should have one entry and one exit

## Reference
Clean code

