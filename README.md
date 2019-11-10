# 자료구조 설명 및 예제

## 1. 리스트(List)

### *리스트의 정의

#### 어레이 사이즈를 미리 지정하는 정적인 어레이와는 달리 데이터가 들어올때 마다 동적으로 메모리를 할당하는 자료구조
|                |어레이|리스트|
|----------------|------|-----|
|메모리 할당 효율 |      |   O |
|데이터 저장 값   |   O  |     |
|중간 값 추가/삭제|      |   O |

![Linkedlist](https://www.geeksforgeeks.org/wp-content/uploads/gq/2013/03/Linkedlist.png)

### *리스트의 종류

### -Singly Linked List
##### 노드안에 링크가 1개이고 단방향으로 진행하는 리스트

### -Doubly Linked List
#### 노드안에 링크가 2개이고 양방향으로 진행할 수 있는 리스트

### -Circular Linked List
#### 마지막 노드가 첫 번째 노드를 가르켜서 계속 회전할 수 있게 만들어진 리스트

### *리스트 예제

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


## 트리(Tree)

### *트리의 정의

#### 부모 노드 밑에 여러 자식 노드가 연결되고, 자식 노드 각각에 다시 자식 노드가 연결되는 재귀적 형태의 자료구조다.

![tree](https://upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Sorted_binary_tree_ALL.svg/400px-Sorted_binary_tree_ALL.svg.png)

### *트리의 순회방법에 따른 분류

#### -Pre-orde Traversal


### *트리의 종류

#### -Binary tree
##### 최대로 많이 가진 자식노드의 수가 2개를 넘지않는 트리

#### -Binary search tree
##### 왼쪽에서 오른쪽으로 갈 수록 노드값이 커지는 트리

#### -Balance tree
##### 너무 한 쪽으로 치우치지 않은 트리

#### -Complete binary tree
##### 트리에 노드가 가득 차있고, 맨 아래 트리는 맨 왼쪽부터 차례대로 차있는 트리 (맨 아래 오른쪽은 몇개 없어도 상관없음)

#### -Full binary tree
##### 각각의 노드들이 가지고 있는 자식노드가 둘있거나 아예 없는 트리

### *트리 예제

#### 트리 출력
>.... 5  ....

>..3.. ...7

>.............8
``` 
#include <stdio.h>
#include <stdlib.h>               /* malloc */
typedef struct Tree {
    struct Tr *l, *r;
    int d;
} T;
void print(T* p){                 // 재귀함수라 생각하면 쉬움
   printf("%d\n", p->d);
   if(p->l) print(p->l);
   if(p->r) print(p->r);    
}
T* mem(){                        //
 T* p=(T*)malloc(sizeof(T));
 p->l=p->r=NULL;
 return(p);
}
int main(void){                     // 트리 생성
    T *r, *r1, *r2, *l1;
    l1= (T*)mem(); l1->d=3; 
    r2= (T*)mem(); r2->d=8; 
    r1= (T*)mem(); r1->d=7; r1->r=r2;
    r= (T*)mem(); r->d=5; r->l=l1;  r->r=r1;
    print(r);
}
```
