# Function to add the current value to memory
def add_memory():
with open('calculator_memory.txt', 'w') as file:
file.write(entry_num1.get())
# Function to read the value from memory
def recall_memory():
try:
with open('calculator_memory.txt', 'r') as file:
memory = file.read()
entry_num1.delete(0, tk.END) # Clear the current entry
entry_num1.insert(0, memory) # Insert the memory value


# Function to clear the memory
def clear_memory():
with open('calculator_memory.txt', 'w') as file:
file.write('')
def perform_calculation(operation):
num1 = float(entry_num1.get())
num2 = float(entry_num2.get())
result = 0
if operation == '+':
result = num1 + num2
elif operation == '-':
result = num1 - num2
elif operation == '*':
result = num1 * num2
elif operation == '/':
try:
result = num1 / num2
except ZeroDivisionError:
result = "Error: Division by zero."
entry_num1.delete(0, tk.END) # Clear the first entry
entry_num1.insert(0, str(result)) # Display the result for next operation
# Create the main window
root = tk.Tk()
root.title("Calculator with Memory")
# Create the entry widgets for numbers
entry_num1 = tk.Entry(root)
entry_num1.pack()
entry_num2 = tk.Entry(root)
entry_num2.pack()
# Create the buttons for each operation and memory functions
tk.Button(root, text="+", command=lambda: perform_calculation('+')).pack()
tk.Button(root, text="-", command=lambda: perform_calculation('-')).pack()
tk.Button(root, text="*", command=lambda: perform_calculation('*')).pack()
tk.Button(root, text="/", command=lambda: perform_calculation('/')).pack()
tk.Button(root, text="M+", command=add_memory).pack()
tk.Button(root, text="MRC", command=recall_memory).pack()
tk.Button(root, text="MC", command=clear_memory).pack()
# Label to display the result or instructions
tk.Label(root, text="Enter values and choose operation.").pack()
