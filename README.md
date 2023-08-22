# File Encryption/Decryption Tool

This is a simple program that allows you to encrypt or decrypt files using a specified key.

## Usage

1. Choose whether you want to encrypt or decrypt a file.

2. Enter the input file name.

3. Enter the output file name.

4. Enter the encryption/decryption key.

5. The program will then encrypt or decrypt the file based on your choice and the provided key.

## Example

```cpp
#include <iostream>
#include <fstream>
#include <string>
#include <vector>
#include <algorithm>

// Encryption function
void encryptDecrypt(std::ifstream &inputFile, std::ofstream &outputFile, const std::string &key) {
    char ch;
    size_t keyLength = key.length();
    size_t i = 0;

    while (inputFile >> std::noskipws >> ch) {
        ch = ch ^ key[i % keyLength];
        outputFile << ch;
        i++;
    }
}

int main() {
    std::string inputFile, outputFile, key;
    int choice;

    std::cout << "File Encryption/Decryption Tool\n";
    std::cout << "1. Encrypt\n";
    std::cout << "2. Decrypt\n";
    std::cout << "Enter your choice: ";
    std::cin >> choice;

    std::cout << "Enter input file name: ";
    std::cin >> inputFile;
    std::cout << "Enter output file name: ";
    std::cin >> outputFile;
    std::cout << "Enter encryption/decryption key: ";
    std::cin >> key;

    std::ifstream inFile(inputFile, std::ios::binary);
    std::ofstream outFile(outputFile, std::ios::binary);

    if (!inFile || !outFile) {
        std::cerr << "Error opening files.\n";
        return 1;
    }

    if (choice == 1) {
        encryptDecrypt(inFile, outFile, key);
        std::cout << "File encrypted successfully.\n";
    } else if (choice == 2) {
        encryptDecrypt(inFile, outFile, key);
        std::cout << "File decrypted successfully.\n";
    } else {
        std::cerr << "Invalid choice.\n";
        return 1;
    }

    inFile.close();
    outFile.close();

    return 0;
}
```

## Disclaimer

This program is provided as-is without any warranty. Use at your own risk.

## License
This project is licensed under the [MIT License](LICENSE).

© Copyright [2023] NotYourAnonOne

