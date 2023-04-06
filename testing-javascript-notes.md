# TESTING WITH JEST

## ASSERTION OPTIONS FOR TESTING IN JAVASCRIPT W/ JEST

1. `expect(value)`                              - method creates an expectation for a value to match the assertion
2. `toBe(value)`                                - assertion checks if the value is strictly equal to the expected value
3. `toEqual(value)`                             - assertion checks if the value is equal to the expected value
4. `toMatch(regexpOrString)`                    - assertion checks in the value matches the regular expression or string
5. `toContain(item)`                            - assertion checks if an array or string contains the expected item
6. `toBeGreaterThan(number)`                    - assertion checks if the value is greater than the expected number
7. `toBeLessThan(number)`                       - assertion checks if the value is less than the expected number
8. `toThrow(error)`                             - assertion checks if the function throws an error
9. `not`                                        - modifier can be used with any of the above assertions to check the opposite of the expectation
10. `toBeInstanceOf(class)`                     - assertion checks if an object is an instance of a particular class
11. `toHaveLength(length)`                      - assertion checks if an array or string has the expected length
12. `toHaveProperty(propertyPath, value?)`      - assertion chedks if an object has the expected property, and optionally, if the property has the expected value
13. `toBeCloseTo(number, decimalPlaces)`        - assertion checks if the value is close to the expected number, within a certain number of decimal places
14. `toBeNaN()`                                 - assertion checks if the value is NaN
15. `toThrowError(error?)`                      - assertion checks if the function throws an error of a specific type
16. `toMatchObject(object)`                     - assertion checks if an object contains all the expected properties and values, regardless of any additional properties that may be present
17. `toBeCalled()`                              - assertion checks if a mock function was called
18. `toHaveBeenCalled()`                        - assertion checks if a mock function was called at least once
19. `toHaveBeenCalledWith(arg1, arg2, ...)`     - assertion checks if a mock function was called with specific arguments
20. `not.toBe(value)`                           - assertion checks if the value is not strictly equal to the expected value
21. `not.toEqual(value)`                        - assertion checks if the value is not equal to the expected value
22. `toThrow(message?)`                         - assertion checks if a function throws an error; optionally specify the error message that should be thrown
23. `toHaveReturned()`                          - assertion checks if a function returns a value
24. `toHaveReturnedTimes(times)`                - assertion checks if a function has returned a value a specific number of times
25. `toHaveReturnedWith(value)`                 - assertion checks if a function has returned a specific value
26. `toHaveBeenLastCalledWith(arg1, arg2, ...)` - assertion checks if a mock function was last called with specific arguments
27. `toBeNull()`                                - assertion checks if the value is null
