# Caesar Cipher

The Caesar Cipher is one of the earliest and simplest encryption methods, named after Julius Caesar, who used it to secure his military messages. This cipher involves shifting each letter in the alphabet by a set number of positions. For instance, with a shift of three, ‘A’ becomes ‘D’, ‘B’ becomes ‘E’, and so forth. While straightforward, the Caesar Cipher laid the foundation for modern cryptographic practices. In this article, we’ll delve into the mechanics of the Caesar Cipher, its historical importance, and its influence on cryptography, including its strengths and weaknesses.

### Algorithm for Caesar Cipher

**Input:**

1. Select a shift value between 1 and 25.
2. Write down the alphabet in order from A to Z.
3. Create a shifted alphabet by moving each letter in the original alphabet forward by the chosen shift value. For example, with a shift of 3:
   - Original alphabet: A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
   - Shifted alphabet:  D E F G H I J K L M N O P Q R S T U V W X Y Z A B C
4. For encryption, replace each letter in the original message with its corresponding letter in the shifted alphabet. For instance, if the shift value is 3, “hello” becomes “khoor.”
5. For decryption, shift each letter in the encrypted message backwards by the same shift value. For example, with a shift of 3, “khoor” reverts to “hello.”

Code

Here is the Python code for the Caesar Cipher:

def caesar_cipher(message, shift_value, action='encrypt'):
    result_text = ""
    shift_value = shift_value if action == 'encrypt' else -shift_value

    for letter in message:
        if letter.isalpha():
            ascii_base = ord('A') if letter.isupper() else ord('a')
            shifted_char = chr((ord(letter) - ascii_base + shift_value) % 26 + ascii_base)
            result_text += shifted_char
        else:
            result_text += letter

    return result_text


def main():
    print("Welcome to the Caesar Cipher Program!")
    action = input("Select action: (e)ncrypt or (d)ecrypt: ").lower()
    text = input("Enter the text: ")
    shift_value = int(input("Enter shift amount: "))

    if action == 'e':
        result = caesar_cipher(text, shift_value, 'encrypt')
    elif action == 'd':
        result = caesar_cipher(text, shift_value, 'decrypt')
    else:
        print("Invalid action selected.")
        return

    print(f"Output: {result}")


if __name__ == "__main__":
    main()
