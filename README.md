# EEL-Activity-6
#include <stdio.h>
#include <string.h>

struct RTO {
    char prefix[5];
    char city[20];
    char state[20];
    char zone[20];
    char message[50];
};

int main() {
    struct RTO data[] = {
        {"MH12", "Pune",    "Maharashtra", "Eco Zone",      "Known for clean tech and green initiatives!"},
        {"MH14", "Pimpri",  "Maharashtra", "Industrial Zone","A major hub for manufacturing."},
        {"DL01", "New Delhi","Delhi",      "Heritage Zone", "Full of history and monuments."},
        {"KA03", "Bengaluru","Karnataka",  "Tech Zone",     "India's Silicon Valley!"}
    };

    int size = sizeof(data) / sizeof(data[0]);

    char reg[20];
    printf("Enter Vehicle Registration Number: ");
    scanf("%s", reg);

    // Basic validation
    if (strlen(reg) < 4) {
        printf("Invalid registration number format.\n");
        return 0;
    }

    // Extract prefix (first 4 characters)
    char prefix[5];
    strncpy(prefix, reg, 4);
    prefix[4] = '\0';

    // Search for prefix
    int found = 0;
    for (int i = 0; i < size; i++) {
        if (strcmp(prefix, data[i].prefix) == 0) {
            found = 1;
            printf("\n--- Vehicle Location Details ---\n");
            printf("Registration Prefix : %s\n", prefix);
            printf("City                : %s\n", data[i].city);
            printf("State               : %s\n", data[i].state);
            printf("Zone                : %s\n", data[i].zone);
            printf("Message             : %s\n", data[i].message);
            break;
        }
    }

    if (!found) {
        printf("No location found for the given registration number.\n");
    }

    return 0;
}
