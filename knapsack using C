#include <stdio.h>
#include <stdlib.h>
typedef struct {
    float weight;
    float profit;
    float ratio;
} Item;
typedef struct Node {
    int level;
    int profit;
    int weight;
    float bound;
} Node;
int compare(const void* a, const void* b) {
    Item* i1 = (Item*)a;
    Item* i2 = (Item*)b;
    if (i2->ratio > i1->ratio) return 1;
    if (i2->ratio < i1->ratio) return -1;
    return 0;
}
float bound(Node u, int n, int W, Item items[]) {
    if (u.weight >= W) return 0;
    float profit_bound = u.profit;
    int j = u.level + 1;
    int totweight = u.weight;
    while ((j < n) && (totweight + items[j].weight <= W)) {
        totweight += items[j].weight;
        profit_bound += items[j].profit;
        j++;
    }
    if (j < n)
        profit_bound += (W - totweight) * items[j].ratio;
    return profit_bound;
}
int solveKnapsack(int n, int W, Item items[]) {
    qsort(items, n, sizeof(Item), compare);
    Node queue[1000];
    int head = 0, tail = 0;
    Node u, v;
    u.level = -1; u.profit = u.weight = 0;
    u.bound = bound(u, n, W, items);
    queue[tail++] = u;
    int maxProfit = 0;
    while (head < tail) {
        u = queue[head++];
        if (u.level == n - 1) continue;
        v.level = u.level + 1;
        v.weight = u.weight + items[v.level].weight;
        v.profit = u.profit + items[v.level].profit;
        if (v.weight <= W && v.profit > maxProfit)
            maxProfit = v.profit;
        v.bound = bound(v, n, W, items);
        if (v.bound > maxProfit)
            queue[tail++] = v;
        v.weight = u.weight;
        v.profit = u.profit;
        v.bound = bound(v, n, W, items);
        if (v.bound > maxProfit)
            queue[tail++] = v;
    }
    return maxProfit;
}
int main() {
    int n, W;
    printf("Enter number of items and Knapsack capacity: ");
    scanf("%d %d", &n, &W);
    Item* items = (Item*)malloc(n * sizeof(Item));
    for (int i = 0; i < n; i++) {
        printf("Item %d - Profit and Weight: ", i + 1);
        scanf("%f %f", &items[i].profit, &items[i].weight);
        items[i].ratio = items[i].profit / items[i].weight;
    }
    printf("\nMaximum Profit: %d\n", solveKnapsack(n, W, items));
    free(items);
    return 0;
}
