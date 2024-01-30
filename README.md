import string
import random

def generate_password(length=12, use_special_chars=True):
    """
    Generate a random password of the specified length.
    The password will consist of a combination of uppercase letters, lowercase letters, digits, and optionally special characters.
    """
    # Define the character sets to be used in the password
    lowercase_chars = string.ascii_lowercase
    uppercase_chars = string.ascii_uppercase
    digit_chars = string.digits
    special_chars = string.punctuation

    # Combine the character sets into one list
    if use_special_chars:
        password_chars = lowercase_chars + uppercase_chars + digit_chars + special_chars
    else:
        password_chars = lowercase_chars + uppercase_chars + digit_chars

    # Generate the password by randomly selecting characters from the combined character set
    password = ''.join(random.choice(password_chars) for _ in range(length))

    # Ensure that the password contains at least one character from each character set
    while (not any(char in lowercase_chars for char in password) or
           not any(char in uppercase_chars for char in password) or
           not any(char in digit_chars for char in password) or
           (use_special_chars and not any(char in special_chars for char in password))):
        password = ''.join(random.choice(password_chars) for _ in range(length))

    return password

# Example usage
print(generate_password())