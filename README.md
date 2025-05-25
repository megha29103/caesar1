def caesar_encrypt(text, shift):
    result = ""
    for char in text:
        if char.isalpha():
            # Handle uppercase letters
            base = ord('A') if char.isupper() else ord('a')
            # Shift character and wrap around alphabet
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            # Non-alphabetic characters remain unchanged
            result += char
    return result

def caesar_decrypt(text, shift):
    # Decryption is encryption with negative shift
    return caesar_encrypt(text, -shift)

def main():
    print("Caesar Cipher Encryption and Decryption")
    message = input("Enter your message: ")
    while True:
        try:
            shift = int(input("Enter shift value (integer): "))
            break
        except ValueError:
            print("Invalid input. Please enter an integer value for shift.")

    while True:
        choice = input("Type 'e' to encrypt or 'd' to decrypt: ").strip().lower()
        if choice == 'e':
            encrypted = caesar_encrypt(message, shift)
            print(f"Encrypted message: {encrypted}")
            break
        elif choice == 'd':
            decrypted = caesar_decrypt(message, shift)
            print(f"Decrypted message: {decrypted}")
            break
        else:
            print("Invalid choice. Please enter 'e' or 'd'.")

if __name__ == "__main__":
    main()

