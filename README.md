#include <iostream>
#include <iomanip>
#include "perfect_numbers.h"

int main() {
    // Валидация на входните данни (Изискване 4)
    int n;
    std::cout << "--- Perfect Numbers Project ---\n";
    std::cout << "Enter how many perfect numbers to find (1-8): ";

    if (!(std::cin >> n) || n <= 0) {
        std::cerr << "Error: Please enter a positive integer!" << std::endl;
        return 1;
    }

    if (n > 8) {
        std::cout << "Limiting to 8 due to memory limits.\n";
        n = 8;
    }

    // Генериране на резултатите
    std::vector<ull> perfects = store_n_perfect_mersenne(n);
    std::vector<std::string> formulas = store_n_perfect_strings(n);

    // Извеждане (Изискване 3)
    std::cout << "\nResults:\n";
    std::cout << std::left << std::setw(5) << "ID"
        << std::setw(25) << "Perfect Number"
        << "Formula" << std::endl;
    

    for (int i = 0; i < n; i++) {
        std::cout << std::left << std::setw(5) << (i + 1)
            << std::setw(25) << perfects[i]
            << formulas[i] << std::endl;
    }

    return 0;
}
