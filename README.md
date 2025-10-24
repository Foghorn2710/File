#include <stdio.h>
#include <stdlib.h>

typedef struct{
    char *dayName;
    int date;
    char *activity;
}Day;

void create(Day *day) {
    day🡪dayName = (char *)malloc(sizeof(char) * 20);
    day🡪activity = (char *)malloc(sizeof(char) * 100);

    printf("Enter the day name: ");
    scanf("%s", day🡪dayName);

    printf("Enter the date: ");
    scanf("%d", &day🡪date);

    printf("Enter the activity for the day: ");
    scanf(" %s", day🡪activity);
}

void read(Day *calendar, int size) {
    int i;
    for (i = 0; i < size; i++) {
        printf("Enter details for Day %d:\n", i + 1);
        create(&calendar[i]);
    }
}

void display(Day *calendar, int size) {
    int i;
    printf("\nWeek's Activity Details:\n");
    for (i = 0; i < size; i++) {
        printf("Day %d:\n", i + 1);
        printf("Day Name: %s\n", calendar[i].dayName);
        printf("Date: %d\n", calendar[i].date);
        printf("Activity: %s\n", calendar[i].activity);
        printf("\n");
    }
}


int main() {
    int size;
    Day *calendar;
    printf("Enter the number of days in the week: ");
    scanf("%d", &size);

    calendar = (Day *)malloc(sizeof(Day) * size);

    if (calendar == NULL) {
        printf("Memory allocation failed. Exiting program.\n");
        return 1;
    }

    read(calendar, size);
    display(calendar, size);

    return 0;
}
