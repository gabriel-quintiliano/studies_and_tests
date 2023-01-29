// This program will get every string you type as command line argument and hash it into a hashmap, and then
// print all the linked list in this hashmap, which were yielded from the hashing process

// if you just don't want to tip a bunch of command line arguments as words to be add
// to the hashmap (map), use the line of code bellow

// ./hashmap cabelo calo carro roupa saia calça pia gato cachorro prato galinha luva vaca veado computador macaco carroça mesa mato capim fogão panela zarkos thor mike cadeira sbp sapo sapato chinelo cama tv celular


#include <stdio.h>
#include <stdbool.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>

typedef struct node
{
    struct node *next;
    char *word;
}
node;

int ALPHABET_SIZE = 26;

bool add(node **list, char *string);
void free_map(node **map);
void print_map(node **map);
void hash(node **map, char *word);

int main(int argc, char *argv[])
{
    // map is a pointer that holds the address of a dinamically allocated array
    // of ALPHABET_SIZE elements (26), which are pointers to nodes
    node **map = calloc(ALPHABET_SIZE, sizeof(node *));
    if (map == NULL)
    {
        printf("An error occured with allocation of memory for map");
        return 0;
    }

    for (int x = 1; x < argc; x++)
    {
        char *word = argv[x];
        hash(map, word);
    }

    printf("\n");

    print_map(map);
    free_map(map);

    return 0;
}

// This hash function will hash the argument word and then add it to the map in the correct index
// according to the yielded hash code from word
void hash(node **map, char *word)
{
    // the hashing itself consists int lowering the case of the first letter of word and then
    // subtraction 97 of its ascii value so that it binds 'a' to 0, 'b' to 1, 'c' to 3, and so on
    int hashcode = tolower(word[0]) - 97;

    // According to the hashcode yielded we'll add word to the linked list in the corresponding
    // index in map. If we couldn't add it correctly, then we free the whole list and terminate
    // the execution of the program (echoing the value 1 as it was the return from main())
    if (add(&map[hashcode], word) == false)
    {
        free_map(map);
        exit(1);
    }
}

// this function will add a new element (in this case a string) in the list received as an argument
// It's important to notice that as we want to pemanently alterate the address to which list points
// to, when can't write a parameter like "node *list", or this function would just be receiving the
// the value of list, hence, the address it currently points to, so, to avoid that we must write
// "node **list" so we received the address where list is declared (so, technically speaking, a
// an address(*) of an address(*) of a node), so we can alterate the address that's written there,
// aka the address held by the pointer list itself, the address it points to
bool add(node **list, char *string)
{
    // temporary pointer for safely dealing with the new block of memory, until assingning it the root of the list
    node *tmp = malloc(sizeof(node));
    // malloc-ing space for safely dealing with the string passad as an argument, until assigning it to
    // word member of the new node
    char *w = malloc(strlen(string) + 1);

    // if either of the allocations went wrong, we'll right way return false and stop
    if (tmp == NULL || w == NULL)
    {
        return false;
    }

    // strcpy is coping string to the block of memory w, and then returning the address of w, which
    // is being assined to the word member of the node tmp.
    tmp->word = strcpy(w, string);
    // I did this way intead of strcpy(tmp->word, string), because this way I can check on the allocation
    // of tmp and w at the same time with only one if, if I had done it differently, this function would
    // have had second if. The first if would still be checking on tmp, then we'd malloc space directly
    // for tmp->word, the sencond if would check on tmp->word for finally the assignment of string to word
    // I went went for a more aesthetic code, maybe a tiny bit more efficient.

    // Here we assing to tmp->next the value of the current first node of the the linked list
    tmp->next = *list;
    // Lastly, we just assing to the list pointer the address of the new (first) node of the linked list
    *list = tmp;
    // it has to be done this way with *list intead of just list, because this way we're accessing
    // the actual block of memory of list and writing the new address it'll point to
    // meanwhile list points to the address that has another address of a node (list == node **)

    return true;
}

// this funtion will print every linked list in the dynamic array map
void print_map(node **map)
{
    // First it iterates through the evry alphabet letter aka every hashcode possible aka
    // every index of the map dynamic array
    for (int i = 0; i < ALPHABET_SIZE; i++)
    {
        // then, just for easier manipulation, it isolates the list inside map
        node *list = map[i];

        if (list != NULL)
        {
            // if the list is not empty, it will iterate until the NULL value aka the end of the list
            // printing each string in the linked list, and if it's not the actual last node, just for
            // stylistic purposes, it'll also print " --> "
            for (node *tmp = list; tmp != NULL; tmp = tmp->next)
            {
                printf("%s (%lu)", tmp->word, strlen(tmp->word));
                if (tmp->next != NULL)
                {
                    printf(" --> ");
                }
            }
            printf("\n\n");
        }
    }
}

// In case any allocation goes wrong or the program reached its end, this function will deal
// with freeing every dynamically allocated block of memory
void free_map(node **map)
{
    // simmilar to the print_map function above, first it isolates a list, then deals with
    // with every possible element of the linked list and finally frees the map array
    for (int i = 0; i < ALPHABET_SIZE; i++)
    {
        node *list = map[i]; // isolates a list according to index in map

        for (node *tmp = list; tmp != NULL; tmp = list)
        {
            list = list->next; // gets the address of the node next to the current node (tmp)
            free(tmp->word); // frees the word member of the node (which holds a string)
            free(tmp); // frees the whole current node
        }
    }

    free(map); // frees the whole dinamically allocated map array
}
