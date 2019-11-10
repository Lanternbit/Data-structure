# 자료구조 설명 및 예제

## 1. 리스트(List)

### *리스트의 정의

#### 어레이 사이즈를 미리 지정하는 정적인 어레이와는 달리 데이터가 들어올때 마다 동적으로 메모리를 할당하는 자료구조

![Alt text](C:\anu\Linkedlist.png)

### *리스트의 종류

### -Singly Linked List
##### 노드안에 링크가 1개이고 단방향으로 진행하는 리스트

### -Doubly Linked List
#### 노드안에 링크가 2개이고 양방향으로 진행할 수 있는 리스트

### -Circular Linked List
#### 마지막 노드가 첫 번째 노드를 가르켜서 계속 회전할 수 있게 만들어진 리스트

### 리스트 예제

```
#include <stdio.h>
#include <stdlib.h>
typedef struct list {
 int d;
 struct list* p;
} LIST;
LIST* root = NULL;
LIST* last = NULL;
void AddList(int a){
 LIST* r = (LIST*)malloc(sizeof(LIST));
 r->d = a;
 r->p = NULL;
 if(root==NULL) root = r;
 else           last->p = r;
 last = r;
}
int main(void){
 AddList(35);
 AddList(40);
 AddList(45);
 while(root){
  printf("%d\n", root->d);
  root = root->p;
 }
}
```
