# Sayook-ASE-Coding
General Problem Solving
1 Am i perfect

def classify_number(num):
    factors_sum = 0
    for i in range(1, num):
        if num % i == 0:
            factors_sum += i
    
    if factors_sum == num:
        return "Perfect"
    elif factors_sum > num:
        return "Abundant"
    else:
        return "Deficient"

print(classify_number(6))
print(classify_number(12))
print(classify_number(8))

3 problem
def steps_to_one(x):
    steps = 0
    while x != 1:
        if x % 2 == 0:
            x //= 2
        else:
            x = 3 * x + 1
        steps += 1
    return steps


print(steps_to_one(12))  

Medium 
2.Hide The Pin
def convert_pin(pin):
    binary_str = bin(pin)[2:] 
    binary_str = binary_str[::-1] 
    
    conversion_table = {
        '1': 'pop',
        '10': 'double rip',
        '100': 'hide your mints',
        '1000': 'fall',
        '10000': None  # For reverse operation, handled separately
    }
    
    output = []
    reversed_order = False
    
    for part in binary_str.split('0'):
        if part == '':  # Skip empty parts
            continue
        if part == '1' * len(part):  # If all digits are 1's
            reversed_order = True
        else:
            if part in conversion_table:
                output.append(conversion_table[part])
    
    if reversed_order:
        output.reverse()
    
    return output

print(convert_pin(3))
print(convert_pin(19))  

Hard 
2.n-Chai
def generate_tea_order(n, k, g, b):
    order = []
    
    while n > 0:
        if g > b:
            if len(order) >= k and order[-k:] == ['Green'] * k:
                order.append('Black')
                b -= 1
                n -= 1
            else:
                order.append('Green')
                g -= 1
                n -= 1
        else:
            if len(order) >= k and order[-k:] == ['Black'] * k:
                order.append('Green')
                g -= 1
                n -= 1
            else:
                order.append('Black')
                b -= 1
                n -= 1
    
    return order


print(generate_tea_order(5, 1, 3, 2)) 
print(generate_tea_order(4, 3, 4, 0))  

