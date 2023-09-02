# Dec-Binary-Conversion

//Decimal to Binary and Binary to Decimal functions

#include <iostream>
#include <string>
using namespace std;

int number, result;
string input;

int binarytodecimal(string);

string decimaltobinary(int);

int main () {
 cout << "Enter a number (decimal or binary): ";
 getline (cin, input); //read as string

try {
number = stoi(input); //read string and create int
if (input[0] == '0' && input.length() > 1) { //check if input starts with 0. if 1 and 0s follow --> binary, if others --> not valid.
    int i = 0;
    while (i < input.length()){
        if (input[i] != '0' && input[i] != '1'){
        cout << "This is not a valid binary number.";
        exit(1);
        }
        i++;
    }
    if (input.length() > 9) { //check for 9 bits or less
        cout << "The binary number has more than 9 binary digits.";
        exit(1);
    }
    else { //if we get to this point it must be valid binary
        cout << "Converting binary to decimal. ";
        cout << "The result is " << binarytodecimal(input);
        exit(1);
    }
}
else if (number > 255) { //compares the int version of input to a limit. 
    cout << "This number is outside the range 0 to 255.";
    exit(1);
}
else {//if we get to this point, input must be a valid deimal 
    cout << "Converting decimal to binary. ";
    cout << "The result is " << decimaltobinary(number);
} 
}
catch (const invalid_argument &) { //catches all other inputs, eg. charaters that void stoi()
    cout << "This is not a valid number.";
}
}

//------------------------------------------------FUNCTIONS-------------------------------------------

int binarytodecimal(string binary) {
    int decimal = 0;
    for (int i = 0; i < binary.length(); i++) {
    char c = binary[i];
    decimal = decimal * 2 + (c - '0');
    }
    return decimal;
}

string decimaltobinary(int decimal){
    if (decimal == 0) {
        cout << "The result is 0000 0000."; // Padding with 8 zeros
        exit(1);
    } 
    else { //binary to decimal calculation
        string binary = "";
        while (decimal > 0) {
            binary = to_string(decimal % 2) + binary;
            decimal /= 2;
        }
        while (binary.length() < 8) { // add zeros to ensure 8 bit
            binary = "0" + binary;
        }
        string binary_adjust = "";
        for (int i = 0; i < 4; ++i) {
            binary_adjust += binary[i]; 
        }
        binary_adjust += " "; //add the space after 4bits
        for (int i = 4; i < 8; ++i) {
            binary_adjust += binary[i];//add the rest back on
        }
        return b;
    } 
}
    
