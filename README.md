red_polje.h
===========

Implementacija reda pomoću polja
================================


typedef int element;

struct tpacijent{
       char ime[15], prezime[20];
       int dan, mjesec, godina;
       char spol;
       int dolazak, u_ordinaciji;
       int prioritet;
       int usluga;
       int ordinacija;
       };
       
struct tqueue{
       tpacijent pacijent[10000];
       int front, rear;
       };
       
tqueue *queue = new tqueue;

int AddOne(int n){
    return ((n+1)%10000);
    }

bool IsEmptyQ(tqueue *queue){
     if (AddOne(queue->rear)==queue->front) return 1;
        else return 0;
     }

tpacijent FrontQ(tqueue *queue){
          if (!IsEmptyQ(queue)) return queue->pacijent[queue->front]; 
          }
          
void InitQ(tqueue *queue){
     queue->front=0;
     queue->rear=10000;
     }
     
void DeQueueQ(tqueue *queue){
     if (!IsEmptyQ(queue)) queue->front++;
     }
     
void EnQueueQ(tpacijent x, tqueue *queue){
     if (!(AddOne(AddOne(queue->rear))==queue->front))  {
              if (queue->rear==10000) queue->rear=0;
                 else queue->rear++;
              queue->pacijent[queue->rear]=x;
             }
     }
