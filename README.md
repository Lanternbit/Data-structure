# 자료구조 설명 및 예제

## 1. 리스트(List)

### *리스트의 정의

#### 어레이 사이즈를 미리 지정하는 정적인 어레이와는 달리 데이터가 들어올때 마다 동적으로 메모리를 할당하는 자료구조다.
|                |어레이|리스트|
|----------------|------|-----|
|메모리 할당 효율 |      |   O |
|데이터 저장 값   |   O  |     |
|중간 값 추가/삭제|      |   O |

![Linkedlist](https://www.geeksforgeeks.org/wp-content/uploads/gq/2013/03/Linkedlist.png)

### *리스트의 종류

> 1) Singly Linked List - 노드안에 링크가 1개이고 단방향으로 진행하는 리스트

> 2) Doubly Linked List - 노드안에 링크가 2개이고 양방향으로 진행할 수 있는 리스트

> 3) Circular Linked List - 마지막 노드가 첫 번째 노드를 가르켜서 계속 회전할 수 있게 만들어진 리스트

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


## 2. 트리(Tree)

### *트리의 정의

#### 부모 노드 밑에 여러 자식 노드가 연결되고, 자식 노드 각각에 다시 자식 노드가 연결되는 재귀적 형태의 자료구조다.

![tree](https://upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Sorted_binary_tree_ALL.svg/400px-Sorted_binary_tree_ALL.svg.png)

Depth-first traversal of an example tree: pre-order (red): F, B, A, D, C, E, G, I, H; in-order (yellow): A, B, C, D, E, F, G, H, I; post-order (green): A, C, E, D, B, H, I, G, F.

### *트리의 순회방법에 따른 분류 (위의 이미지 참조)

> -Pre-orde Traversal

> -In-order Traversal

> -Post-order Traversal

> -Level-order Traversal

### *트리의 종류

> 1) Binary tree - 최대로 많이 가진 자식노드의 수가 2개를 넘지않는 트리

> 2) Binary search tree - 왼쪽에서 오른쪽으로 갈 수록 노드값이 커지는 트리

> 3) Balance tree - 너무 한 쪽으로 치우치지 않은 트리

> 4) Complete binary tree - 트리에 노드가 가득 차있고, 맨 아래 트리는 맨 왼쪽부터 차례대로 차있는 트리 (맨 아래 오른쪽은 몇개 없어도 상관없음)

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


## 3. 그래프(Graph)

### *그래프의 정의

#### 그래프는 노드와 간선(Edge)으로 구성된 비선형 데이터 구조다. 노드는 정점(Vertex or Vertices)이라고도하며 간선(Edge)은 그래프의 두 노드를 연결하는 선 또는 호다. 일반적으로 정점은 원으로 표현하고 간선은 화살표나 선분으로 표현한다. 그리고 변의 경우에는 특정한 수치를 가질 수 있는데 이를 가중치(Weighted value)라고 말한다.

![graph](https://www.geeksforgeeks.org/wp-content/uploads/undirectedgraph.png)

### *그래프의 종류

> 1) 유방향 그래프(Directed Graph) - 간선의 방향이 존재하는 그래프 (간선을 화살표로 표시)

> 2) 무방향 그래프(Undirected Graph) - 모든 간선이 방향을 가지지 않는 그래프 (간선을 선분으로 표시)

> 3) 비가중치 그래프 - 모든 간선에 가중치가 없는 그래프

### *그래프의 방식

> 1) 인접 행렬(Adjacency Matrix) - 2차원 배열을 사용하는 방식

> 2) 인접 리스트(Adjacency List) - 리스트를 사용하는 방식

### *그래프 예제

```
int a[1000][1000]; // 노드가 1000개 존재한다고 가정 1000 * 1000
int n, m; // n = 노드의 갯수, m = 간선의 갯수
int main(void) {
  scanf_s("%d %d", &n, &m); // 노드의 갯수과 간선의 갯수를 입력 받습니다.
  for (int i = 0; i < m; i++) { // 간선의 갯수만큼 반복
     int x, y;
     scanf_s("%d %d", &x, &y); // 서로 이어져 있는지 상태를 입력 받는다. ex) 1 2 로 입력할 경우 1 과 2 는 서로 연결이 됐다는 뜻
     a[x][y] = 1;
     a[y][x] = 1; // 방향성이 없기 때문에 서로 이어져 있음을 1 로 표시합니다.
    }
  for (int i = 0; i <= n; i++) {
    for (int j = 0; j <= n; j++) {
        printf("%d ", a[i][j]);
	   }
	   printf("\n"); // 연결되어 있는지 출력하여 확인합니다.
	 }
  system("pause");
}
```

<hr/>

## 소감

### 자료구조에 대해 배운 수업은 이번 학기를 통틀어 가장 내용이 많고 바로 이해가 안가는 수업중 하나였습니다. 하지만 동기들과 함께 협력하여 이해한 부분을 나누고 같이 생각해보면서 개념들이 제 안에 나름 단단하게 자리잡은 것 같아 정말 뿌듯한 과제였습니다. 리스트와 트리는 이제 처음보다 확연하게 개념을 알아냈고, 그래프는 조금의 공부만 부가적으로 한다면 세가지 자료구조가 프로그래밍 공부의 단단한 초석이 되어 저를 지탱해주리라고 생각합니다. 과제를 끝내면서 세가지 자료구조를 알려주신 교수님과 이해시켜준 동기들에게 감사를 전하고 싶습니다. 열심히 하겠습니다.
