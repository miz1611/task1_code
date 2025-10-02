# task1_code
def encrypt(text, shift):
    result = ""
    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            # Shift character and wrap around alphabet
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            result += char
    return result

def decrypt(text, shift):
    return encrypt(text, -shift)

def main():
    print("Caesar Cipher Tool")
    choice = input("Type 'e' to encrypt or 'd' to decrypt: ").strip().lower()
    message = input("Enter your message: ")
    while True:
        try:
            shift = int(input("Enter the shift value (integer): "))
            break
        except ValueError:
            print("Invalid input. Please enter an integer for the shift value.")

    if choice == 'e':
        encrypted = encrypt(message, shift)
        print("Encrypted message:", encrypted)
    elif choice == 'd':
        decrypted = decrypt(message, shift)
        print("Decrypted message:", decrypted)
    else:
        print("Invalid choice, please enter 'e' or 'd'.")

if __name__ == "__main__":
    main()
