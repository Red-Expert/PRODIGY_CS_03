import re

def check_password_strength(password):
    """Check the strength of the given password and provide feedback."""
    
    # Initialize strength variables
    strength = 0
    feedback = []

    # Length check
    if len(password) >= 8:
        strength += 1
    else:
        feedback.append("Password should be at least 8 characters long.")

    # Check for uppercase letters
    if re.search(r'[A-Z]', password):
        strength += 1
    else:
        feedback.append("Password should contain at least one uppercase letter (A-Z).")

    # Check for lowercase letters
    if re.search(r'[a-z]', password):
        strength += 1
    else:
        feedback.append("Password should contain at least one lowercase letter (a-z).")

    # Check for digits
    if re.search(r'\d', password):
        strength += 1
    else:
        feedback.append("Password should contain at least one digit (0-9).")

    # Check for special characters
    if re.search(r'[\W_]', password):
        strength += 1
    else:
        feedback.append("Password should contain at least one special character (e.g., !, @, #, $, etc.).")

    # Assess overall strength
    if strength == 5:
        feedback.append("Password is strong.")
    elif strength >= 3:
        feedback.append("Password is moderate.")
    else:
        feedback.append("Password is weak.")

    return feedback

def main():
    """Main function to run the password complexity checker."""
    password = input("Enter a password to check its strength: ")
    feedback = check_password_strength(password)
    
    print("\nPassword Feedback:")
    for line in feedback:
        print(f"- {line}")

if __name__ == "__main__":
    main()
