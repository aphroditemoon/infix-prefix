#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define MAKS 200

typedef struct Node {
    char data[MAKS];
    struct Node *next;
} Node;

typedef struct {
    Node *top;
} Stack;

void initStack(Stack *s) {
    s->top = NULL;
}

int isStackEmpty(Stack *s) {
    return s->top == NULL;
}

void push(Stack *s, const char *value) {
    Node *newNode = (Node*)malloc(sizeof(Node));
    if (!newNode) {
        printf("Memori penuh!\n");
        return;
    }
    strcpy(newNode->data, value);
    newNode->next = s->top;
    s->top = newNode;
}

int pop(Stack *s, char *output) {
    if (isStackEmpty(s)) {
        strcpy(output, "");
        return 0; // Gagal pop
    }
    Node *temp = s->top;
    strcpy(output, temp->data);
    s->top = temp->next;
    free(temp);
    return 1; // Berhasil pop
}

void peek(Stack *s, char *output) {
    if (isStackEmpty(s)) {
        strcpy(output, "");
        return;
    }
    strcpy(output, s->top->data);
}

int isOperator(char ch) {
    return (ch == '+' || ch == '-' || ch == '*' || ch == '/' || ch == '^');
}

int isAlphanumeric(char ch) {
    return (isalpha(ch) || isdigit(ch));
}

void reverseString(char *str) {
    int i, j;
    char temp;
    for (i = 0, j = strlen(str) - 1; i < j; i++, j--) {
        temp = str[i];
        str[i] = str[j];
        str[j] = temp;
    }
}

int getPriority(char op) {
    if (op == '+' || op == '-') return 1;
    if (op == '*' || op == '/') return 2;
    if (op == '^') return 3;
    return 0;
}

void convertInfixToPrefix(char *infix, char *prefix) {
    Stack operatorStack, operandStack;
    initStack(&operatorStack);
    initStack(&operandStack);
    
    reverseString(infix);
    for (int i = 0; infix[i]; i++) {
        if (infix[i] == '(') infix[i] = ')';
        else if (infix[i] == ')') infix[i] = '(';
    }

    char temp[2] = "";
    char op1[MAKS], op2[MAKS], result[MAKS];

    for (int i = 0; infix[i]; i++) {
        if (isAlphanumeric(infix[i])) {
            temp[0] = infix[i];
            temp[1] = '\0';
            push(&operandStack, temp);
        } else if (infix[i] == '(') {
            temp[0] = infix[i];
            temp[1] = '\0';
            push(&operatorStack, temp);
        } else if (infix[i] == ')') {
            char top[MAKS];
            peek(&operatorStack, top);
            while (!isStackEmpty(&operatorStack) && strcmp(top, "(") != 0) {
                pop(&operatorStack, temp);
                pop(&operandStack, op2);
                pop(&operandStack, op1);
                sprintf(result, "%s%s%s", temp, op1, op2);
                push(&operandStack, result);
                peek(&operatorStack, top);
            }
            pop(&operatorStack, temp); // Pop '('
        } else if (isOperator(infix[i])) {
            char top[MAKS];
            peek(&operatorStack, top);
            while (!isStackEmpty(&operatorStack) && strcmp(top, "(") != 0 &&
                   ((infix[i] != '^' && getPriority(infix[i]) <= getPriority(top[0])) ||
                    (infix[i] == '^' && getPriority(infix[i]) < getPriority(top[0])))) {
                pop(&operatorStack, temp);
                pop(&operandStack, op2);
                pop(&operandStack, op1);
                sprintf(result, "%s%s%s", temp, op1, op2);
                push(&operandStack, result);
                peek(&operatorStack, top);
            }
            temp[0] = infix[i];
            temp[1] = '\0';
            push(&operatorStack, temp);
        }
    }

    while (!isStackEmpty(&operatorStack)) {
        pop(&operatorStack, temp);
        pop(&operandStack, op2);
        pop(&operandStack, op1);
        sprintf(result, "%s%s%s", temp, op1, op2);
        push(&operandStack, result);
    }

    if (!pop(&operandStack, prefix)) {
        strcpy(prefix, "");
    }
    reverseString(prefix);
}

void convertPrefixToInfix(char *prefix, char *infix) {
    Stack s;
    initStack(&s);
    int len = strlen(prefix);

    for (int i = len - 1; i >= 0; i--) {
        if (isAlphanumeric(prefix[i])) {
            char temp[2] = {prefix[i], '\0'};
            push(&s, temp);
        } else if (isOperator(prefix[i])) {
            char op1[MAKS], op2[MAKS], result[MAKS];
            if (!pop(&s, op1) || !pop(&s, op2)) {
                strcpy(infix, "Ekspresi tidak valid");
                return;
            }
            sprintf(result, "(%s%c%s)", op1, prefix[i], op2);
            push(&s, result);
        }
    }

    if (!pop(&s, infix)) {
        strcpy(infix, "Ekspresi tidak valid");
        return;
    }

    if (!isStackEmpty(&s)) {
        strcpy(infix, "Ekspresi tidak valid");
        return;
    }
}

int main() {
    char ekspresi[MAKS], hasil[MAKS];
    int pilihan;

    while (1) {
        printf("Pilihlah operasi yang diinginkan:\n");
        printf("1. Konversi Infix ke Prefix\n");
        printf("2. Konversi Prefix ke Infix\n");
        printf("3. Keluar\n");
        printf("Masukkan pilihan anda:");
        scanf("%d", &pilihan);
        getchar();  

        switch (pilihan) {
            case 1:
                printf("Masukkan ekspresi infix: ");
                fgets(ekspresi, MAKS, stdin);
                ekspresi[strcspn(ekspresi, "\n")] = 0;
                convertInfixToPrefix(ekspresi, hasil);
                printf("Hasil Prefix: %s\n", hasil);
                break;

            case 2:
                printf("Masukkan ekspresi prefix: ");
                fgets(ekspresi, MAKS, stdin);
                ekspresi[strcspn(ekspresi, "\n")] = 0;
                convertPrefixToInfix(ekspresi, hasil);
                printf("Hasil Infix: %s\n", hasil);
                break;

            case 3:
                exit(0);

            default:
                printf("Pilihan tidak valid!\n");
        }
    }

    return 0;
}
