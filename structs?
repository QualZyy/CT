#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX_STR_LEN 256

int registerPerson(char*, long, int, long int, double);
int deletePerson();
int registerRoom();
int deleteRoom();
int registerContamination();
int registerVisit();
int writeToFile();
int readFromFile();

//Person struct
struct person {
    char _name[40];
    long _birthDate;
    int _infected;      //TRUE OR FALSE
    long int _date;
    double _time;
};


//Room visits struct
struct rooms {
    struct person _visitors[900];
    long int _when[900];    
};

struct person personRegister[1000]; //Register of all registered people
int registeredPersons = 0;

int main() {
    int exit = 0;
    while(!exit) {
        printf("\n\n\n-*-*-*-*-   CoronaTracker (CT)   -*-*-*-*-\n");
        printf("Enter corresponding number to what you want to do\n1.Register ");
        printf("new person\n2.Delete person\n3.Register new room\n4.Delete room\n5.Register contamination");
        printf("\n6.Register visit\n7.Write to file\n8.Read from file\n9.Print Whole Database\n10.Exit\n");

        int option;
        scanf("%i", &option);

        switch(option) {
            case 1: //Register new person
                printf("Enter name");
                char name[40];
                scanf("%s", &name);
                printf("Enter date of birth YYYYMMDD");
                long birthDate;
                scanf("%li", &birthDate);
                
                if(registerPerson(name, birthDate)) {
                    printf("Person was successfully added!");
                } else {
                    printf("An error occured");
                }
                break;

            case 2: //Delete person

                break;

            case 3: //Register room

                break;

            case 4: //Delete room

                break;

            case 5: //Register contamination

                break;

            case 6: //Register a visit

                break;

            case 7: //Write to file

                break;

            case 8: //Read from file
                readFromFile();
                break;

            case 9:
                for(int i=0; i<10; i++) {
                    printf("%s", personRegister[i]);
                }
                break;

            case 10:
                exit = 1;
                break;
            
            case 69:
                printf("Nice");
                break;

            default:
                printf("wtf");
                break;
        }
    }
    return 0;
}

int registerPerson(char name[40], long dateOfBirth, int inf, long int date, double time) {
    if(name == "" || dateOfBirth <= 0) {
        return 0;
    }
    strcpy(personRegister[registeredPersons]._name, name);
    personRegister[registeredPersons]._birthDate = dateOfBirth;
    personRegister[registeredPersons]._infected = inf;
    personRegister[registeredPersons]._date = date;
    personRegister[registeredPersons]._time = time;
    registeredPersons++;
    return 1;
}

int readFromFile() {
    FILE *f;
    char *buf = malloc(MAX_STR_LEN);

    if (buf == NULL) {
        printf ("No memory\n");
        return 0;
    }

    if ((f = fopen("klasse.txt", "r+")) == NULL) {
        printf( "File could not be opened.\n" );
        return 0;
    }

    int i = 0;
    while (fgets(buf, 50, (FILE*) f)) {
        //Starter på ny person/linje
		char * attributeValue;
		attributeValue = strtok(buf, ";"); //Henter hver info, steg for steg
		int attributeNr = 0;
        while (attributeValue != NULL) { 
            //Går gjennom hver attributt i fil
			if(attributeNr == 0) 
				strcpy(personRegister[registeredPersons]._name, attributeValue);
			
			if(attributeNr == 1)
				personRegister[registeredPersons]._birthDate = (long) attributeValue;
			
			if(attributeNr == 2)
				personRegister[registeredPersons]._infected = (int) attributeValue;

            if(attributeNr == 3)
				personRegister[registeredPersons]._date = (long) attributeValue;

            if(attributeNr == 4) //Double e apparently en pain in the ass
				personRegister[registeredPersons]._time = strtod(attributeValue, NULL);
			
			attributeValue = strtok(NULL, ";");
			attributeNr++;
		}
		i++;
	}  
    fclose(f);
    return 1;
}

