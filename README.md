#votingsytem.c
#include <stdio.h>

#define NUM_CANDIDATES 5

// Global candidate list and vote counters
char *candidates[NUM_CANDIDATES] = {
    "ramaroa",
    "Babu",
    "rudra",
    "pawan kalyan",
    "prabhas"
};

int votes[NUM_CANDIDATES] = {0};
 
// Display candidates
void displayCandidates() {
    printf("\nCandidates:\n");
    for (int i = 0; i < NUM_CANDIDATES; i++) {
        printf("%d. %s\n", i + 1, candidates[i]);
    }
}

// Cast a vote
void castVote() {
    int choice;
    printf("Enter candidate number: ");
    scanf("%d", &choice);

    if (choice >= 1 && choice <= NUM_CANDIDATES) {
        votes[choice - 1]++;
        printf("Vote recorded!\n");
    } else {
        printf("Invalid choice! Vote not counted.\n");
    }
}

// Display results and determine winner or tie
void displayResults() {
    printf("\n--- Voting Results ---\n");
    for (int i = 0; i < NUM_CANDIDATES; i++) {
        printf("%s: %d votes\n", candidates[i], votes[i]);
    }

    // Find highest vote count
    int maxVotes = 0;
    for (int i = 0; i < NUM_CANDIDATES; i++) {
        if (votes[i] > maxVotes) {
            maxVotes = votes[i];
        }
    }

    // Count how many candidates have this max vote count
    int countMax = 0;
    for (int i = 0; i < NUM_CANDIDATES; i++) {
        if (votes[i] == maxVotes) {
            countMax++;
        }
    }

    // If no votes at all
    if (maxVotes == 0) {
        printf("No votes cast.\n");
        return;
    }

    // If more than one candidate has the same highest votes -> TIE
    if (countMax > 1) {
        printf("\nResult: It's a TIE between:\n");
        for (int i = 0; i < NUM_CANDIDATES; i++) {
            if (votes[i] == maxVotes) {
                printf("- %s (%d votes)\n", candidates[i], votes[i]);
            }
        }
    } else {
        // Single winner
        for (int i = 0; i < NUM_CANDIDATES; i++) {
            if (votes[i] == maxVotes) {
                printf("\nWinner: %s with %d votes.\n", candidates[i], maxVotes);
                break;
            }
        }
    }
}

int main() {
    int numVoters;

    printf("Enter number of voters: ");
    scanf("%d", &numVoters);

    displayCandidates();

    for (int i = 0; i < numVoters; i++) {
        printf("\nVoter %d:\n", i + 1);
        castVote();
    }

    displayResults();

    return 0;
}


<img width="432" height="867" alt="image" src="https://github.com/user-attachments/assets/474fd006-d468-4dda-bd0f-0eb731927fe3" />



