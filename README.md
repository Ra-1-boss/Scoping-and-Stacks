# Scoping
# Global scope
global_var = "I'm global"
builtin_var = len  # Built-in scope (using len() function)

def outer_function():
    # Enclosing scope
    enclosing_var = "I'm enclosing"
    
    def inner_function():
        # Local scope
        local_var = "I'm local"
        print(local_var)               # Local variable
        print(enclosing_var)           # Enclosing variable
        print(global_var)              # Global variable
        print(builtin_var([1, 2, 3]))  # Built-in function (len)
        
        # Demonstrating name resolution order
        x = "local x"
        print("\nName resolution order (LEGB):")
        print(f"Local x: {x}")         # Finds local x first
        
    inner_function()
    
    # Uncommenting this would cause an error - local_var is not accessible here
    # print(local_var)  

outer_function()

# Global variables are accessible here
print("\nIn global scope again:")
print(global_var)
print(builtin_var("hello"))  # Built-in len function

# Demonstrating global keyword
def modify_global():
    global global_var  # Declare we want to use the global variable
    global_var = "Modified global value"

modify_global()
print("\nAfter modify_global():")
print(global_var)

# Demonstrating nonlocal keyword
def outer():
    x = "original outer value"
    
    def inner():
        nonlocal x  # Refers to x in the enclosing scope
        x = "modified outer value"
    
    print("\nBefore inner():", x)
    inner()
    print("After inner():", x)

outer()
