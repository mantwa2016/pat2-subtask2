# pat2-subtask2
#include <iostream>
#include <map>
#include <string>

using namespace std;

// Morse code mapping
map<char, string> morseCode = {
    {'A', ".-"},    {'B', "-..."},  {'C', "-.-."},
    {'D', "-.."},   {'E', "."},     {'F', "..-."},
    {'G', "--."},   {'H', "...."},  {'I', ".."},
    {'J', ".---"},  {'K', "-.-"},   {'L', ".-.."},
    {'M', "--"},    {'N', "-."},    {'O', "---"},
    {'P', ".--."},  {'Q', "--.-"},  {'R', ".-."},
    {'S', "..."},   {'T', "-"},     {'U', "..-"},
    {'V', "...-"},  {'W', ".--"},   {'X', "-..-"},
    {'Y', "-.--"},  {'Z', "--.."},
    {'0', "-----"}, {'1', ".----"}, {'2', "..---"},
    {'3', "...--"}, {'4', "....-"}, {'5', "....."},
    {'6', "-...."}, {'7', "--..."}, {'8', "---.."},
    {'9', "----."},
    {' ', " "} // Preserve spaces for word separation
};

string convertToMorse(string message) {
    string morse = "";

    for (char ch : message) {
        ch = toupper(ch);
        if (morseCode.find(ch) != morseCode.end()) {
            for (char symbol : morseCode[ch]) {
                if (symbol == '.') morse += (char)46; // dot
                else if (symbol == '-') morse += (char)45; // dash
            }
            morse += ' '; // separate characters by space
        }
    }
    return morse;
}

int main() {
    string input;
    cout << "Enter a short message: ";
    getline(cin, input);

    string morseMessage = convertToMorse(input);
    cout << "Morse Code: " << morseMessage << endl;

    return 0;
}
