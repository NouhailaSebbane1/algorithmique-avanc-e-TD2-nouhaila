# algorithmique-avanc-e-TD2-nouhaila
voici l'implémentation de mes programmes demandés dans le TD 
TD 1:
EXERCICE 1 
           typedef struct {  // Question 1
        int abs;
          int ord;
      } Point;
         Point SaisirPoint() // Question 2
{
Point p;
printf("Donner les coordonnees du point :");
scanf("%d%d",&p.abd,&p.ord);
return p;
}
void AffichePoint(Point p) //Question 3
{
printf("(%d,%d)\n",p.abs,p.ord);
}
//Question 4
#define tmax 20

Point T[tmax]; //un tableau statique 
int taille, i;
// contrainte de la taille
printf("Donner un entier <= %d :",tmax);
scanf("%d",&taille);

// Tableau dynamique
Point *T = NULL;
// Pas de contrainte sur la taille 
printf("Donner un entier :");
scanf("%d",&taille);
T = (Point*)malloc(taille * sizeof(Point));

// Dans les 2 situations (statique ou dynamique)
// remplissage du tableau par des points
 
for(i=0; i < taille ; i++)
{
printf("Donner les coordonnees du point:");
scanf("%d%d", &T[i].abs, &T[i].ord);
}

float distance(Point p) //Question 5
{
return sqrt(p.abs * p.abs + p.ord * p.ord);
}

{
return sqrt(p->abs * p->abs + p->ord * p->ord);
}
//Question 6
void tritab(Point t[], int taille)
{
int i,j;
Point aux;
for(i=0; i<taille-1 ; i++)
for(j = i+1; j<taille ; j++)
if (DistTransVal(t[i]) > DistTransVal(t[j]))
{
aux = t[i];
t[i] = t[j];
t[j] = aux;
}

}
//Question 7
int main(){
Point a;
int i, taille;
a = SaisirPoint();
AfficherPoint(a);
// Tab Statique et Dynamique
Point TStat[TMAX], *TDyn = NULL;
// Lecture de la taille des tableaux 
printf("Donner la taille (<TMAX) du tableau:");
scanf("%d",&taille);
//Allocation memoire pour TDyn 
TDyn = (Point*) malloc(taille * sizeof(Point));
// Remplissage du TStat avec des valeurs aleatoire entre et 100 
srand(time(NULL)); // initiliasation du generateur des aleatoires 
for(i=0; i<taille; i++)
{
TStat[i].x = rand() % 100; TStat[i].y = rand() % 100;
}
// Remplissage du TStat avec des valeurs aleatoire entre et 100 
for(i=0; i<taille; i++)
{
TDyn[i].x = rand() % 100; TDyn[i].y = rand() % 100;
}
// Affichage du TStat 
for(i=0; i<taille; i++) AfficherPoint(TStat[i]);
// Affichage du TDy 
for(i=0; i<taille; i++) AfficherPoint(TDyn[i]);
// le tri
tritab(TDyn, taille);
for(i=0; i<taille; i++) AfficherPoint(TDyn[i]);
return 0;
}


EXERCICE 2:
typedef struct //Question 1
{
int hh;
int mm;
int ss;
} Heure;

int HeureEnSecondes(Heure h)
{
return (h.hh*3600 + h.mm*60 + h.ss);
}
Heure SecondesEnHeure(int sec) //Question 2
{
Heure h;
h.hh = sec/3600;
sec = sec%3600;
h.mm = sec/60;
sec = sec%60;
h.ss = sec;
return h;
}
Heure AddHeures(Heure h1, Heure h2) //Question 3
{
Heure h3;
return (SecondesEnHeure(HeureEnSecondes(h1)+HeureEnSecondes(h2)));
}
TD 2:
#include<stdio.h> // exercice 1
#define N 4
int min(int tab[N])
{
int i;
// premire affectation de index
int index = 0;
// n comparaisons + n-1 affectations
for(i=1; i<N; i++)
{
// n-1 comparaisons
// dans le pire des cas, n-1 affectations
if(tab[i] < tab[index])
index = i;
}
return index;
}
main()
{
int tt[] ={7,4,2,4,2,9};
printf("index du min est = %d\n", min(tt));
}
//— Complexit ́e : T(n) = 1+n+(n-1)+2*(n-1) = 4N-2 ;
//— Ordre : O(n);

// Exercice 2
#define m 3
#define n 3
int MiniMax(int tab[n][m])
{
int i;

//exercice 3
int j;
int max;
int minimax;
// (n) comparaisons
// n -1 affectations
for(i=0; i<n; i++)
{
// n initialisations du max. pour chaque nouvelle ligne
max = tab[i][0];
// (n)*m comparaisons
// (n)(m-1) affectations
for(j=1; j<m; j++)
{
// (n)(m-1) comparaisons
// (n)(m-1) affectations
if(tab[i][j] > max)
max = tab[i][j];
}
// n comparaisons
// 1 affectation
if(i==0)
minimax = max;
// n comparaisons
// (n-1) comparaisons
else if(minimax > max)
minimax = max;
}
return minimax;
}
main(){
int t[3][3] = {{2,3,4},
{5,6,7},
{8,9,10}};
printf("MiniMax = %d\n", MiniMax(t));
}
//— Compexite : T(m,n)=4*m*n+3*n-2 ;
//— Ordre : O(nm), si m = n alors on est en O(n2);

// Exercice 3
 int puissance(a,i)//qestion 1
int puissance(int a,int i)
{
if(i==0)
return 1;
else
return (a*puissance(a,i-1));
}
//exericceee 4
T(0) = 0;
T(1) = 1 + T(0) = 1 ;
T(n) = 1+T(n-1) = 1 + 1 + T(n-2) = n+T(n-n) = n+T(0) = n ;
T(n) = O(n)

int expRapide(int a, int i)
{
if (i==0)
return 1;
else if (i%2 == 0)
return expRapide(expRapide(a,i/2),2);
else return a*expRapide(expRapide(a,i/2),2);
}
//Question  //complexit ́e (en nombre de mutilpications) : On  ́evalue la complexit ́e pour les valeurs de n
//qui sont des puissances de 2 n = 2k.
//Pour n=2, P (puissance) = a *a, 1 multiplication (1=ln(2))
//Pour n=4, P= (a ∗ a)

2, 2 multiplications (2=ln(4))

Pour n=8, P = ((a ∗ a)

2), 3 multiplications (3=ln(8))

pour n = 2k, k multiplications (k=ln(n))
On peut d ́eduire que la complexit ́e est O(ln(n))
5. somme
int somme(int a, int n)
{
if(n==0)
return 1;
else
return (puissance(a,n)+somme(a,n-1));
}
6. complexit ́e :
T(s(a,n)) = T(p(a,n))+T(somme(a,n-1)) + 1 (1 addition)
= T(p(a,n))+T(p(a,n-1))+T(somme(a,n-2)) + 1 +1 (2 additions)
= T(p(a,n))+T(p(a,n-1))+T(p(a,n-2))+T(p(a,n-3))+...+T(p(a,1))+ T(s(a,n-n)) + 1+1+1
.....+1 (n additions)
= n + (n-1) +.....+1 + n = n(n+1)/2 + n
est en O(n2)

6.4 Exercice 4
int rec1(int n)
{
if(n == 0)
return 1;
else
return 2*rec1(n-1);
}

int rec2(int n)
{
if(n == 0)
return 1;
else
return (rec2(n-1) + rec2(n-1));
}
//exericce 4
Le rˆole de la fonction rec1(n)  // question 1
rec1(0)=1 = 20
rec1(1) = 2*rec1(0) = 2 = 21
rec1(2) = 2*rec1(1) = 2*2 = 4 = = 22
rec1(3) = 2*rec1(2) = 2*4 = 8 = 23
.
rec1(n) = 2n
Elle calcule 2n

 Lrec2(0) = 1 = 20 //Question2
rec2(1) = rec2(0) + rec2(0) = 1 + 1 = 2 = 21
rec2(2) = rec2(1) + rec2(1)= 2 + 2 = 22
rec2(3) = rec2(2) + rec2(2) = 4 + 4 = 23
.
rec2(n) = 2n
Elle calcule 2n

 Complexite de rec1(n) //question 3
T1(0) = 0 ; T1(1)=1+T1(0) = 1 ;
T1(n)=1+T1(n-1)=1+1+T1(n-2)=n
La complexite est O(n)
 Complexite de rec2(n)
T2(0) = 0 ; T2(1)=1+2*T2(0)=1 ; //question 4
T2(2) = 1+2*T2(1) = 1 +2
T2(3)= 1+ 2 T2(2) = 1 + 2 + 22
T2(n) = 1+ 2 + 22+.....+2n−1
La somme des n premiers termes d’une suite g ́em ́etrique de raison 2 : T2(n) = (1− 2n)/(1 − 2) =
2n − 1
La complexit ́e est O(2n)

