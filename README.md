# wonbase
this is my first repository.
<br>
Author - zubair (bhao)
# Q  "Two values belonging to different classes need to be exchanged, but the code is not running. What is the problem?"


#include<iostream>
using namespace std;
class y;
class x{
int a;
public:
void setdata(){
cout<<"enter your number"<<endl;
cin>>a;
} 
int getdata(){
    return a;
}
void setdata(int val){
a = val;
}

};
class y{
int b;
public :
friend int   exchange (x&,y&);
void setdata(){

cout<<"enter your number"<<endl;
cin>>b;
} 
int getdata(){
    return b;
}
void setdata(int val ){
    b = val;
}
int exchange (x &oo , y &op){
  
    int temp = oo.getdata();
    oo.setdata(op.getdata());
    op.setdata(temp);
    
    }

};

int main(){
    x oo;
    y op;
    oo.setdata();
    op.setdata();
    cout<<"phela x ki value "<<oo.getdata()<<endl;
    cout<<"phela y ki value"<<op.getdata()<<endl;
int result =  exchange(oo,op);
    cout<<"phela x ki value "<<oo.getdata()<<endl;
    cout<<"phela y ki value"<<op.getdata()<<endl;
    return 0;
}
# Q . 2 " How to add values returned by functions from two separate classes ? "
 
#include<iostream>
using namespace std;
class doma;
class ekma {
int a ;
public :
friend int sum(ekma ,doma );
void setdata(void ){
cout<<"no batao "<<endl;
cin>>a;
}
int  getdata(){
  // ya tarika shi hai value return ka liyab 
  return a;
}
};
class doma {
int b;
public :
friend int sum(ekma,doma);
void setdata(){
cout<<"no batao "<<endl;
cin>>b;
}
int getdata (){
return b;
}
};
int sum(ekma one ,doma two ){
return one.getdata()+two.getdata();

}
int main(){
  ekma one;
  doma two;
one.setdata();
one.getdata();

two.setdata();
cout<<"no jodna hai "<<sum(one ,two )<<endl;

  return 0;
}
# Q . 3 this is an example of multilevel inheritence .
#include<iostream>
using namespace std;
class student {
protected:
int roll_no;
public :
void set_roll_no();
void get_roll_no();

};
void student :: set_roll_no(int r ){
 roll_no = r;
}
void student :: get_roll_no(void){
    cout<<"your roll_no is "<<roll_no<<endl;

}
class marks : public student {
 protected :
 int math ;
 int physics ;
 public :
 void set_subject();
 void get_marks();
};
void marks :: set_subject(int m , int p){
    math = m;
    physics = p;
}
void marks :: get_marks (void ){
    cout<<"math marks is "<<math<<endl;
    cout<<"physics marks is "<<physics<<endl;
}
class result ::  public marks {
public :
void process();
};

void result :: process(){
cout<<"the roll no is "<<roll_no<<endl;
cout<<"math mark "<<math<<endl;
cout<<"physics marks "<<physics <<endl;
cout<<"student result "<<(math+physics)/200*100<<endl;
}
int main(){
result zukks;
zukks.set_roll_no(40);
zukks.set_marks(90,90);
zukks.process();

    return 0;
}
# Q . 4  In  this question we use construction and distruction concept 

#include<iostream>
using namespace std;
class toughness{
static int count =0;
public :
// void toughness(){}
 toughness(){
    count++;
    cout<<"this is a constructor "<<count<<endl;
}
 ~toughness(){
    cout<<"this is a distructor "<<count<<endl;
    count--;
}
};

int main(){
cout<<"enter in the constructor "<<endl;
toughness n1;
toughness n2,n3;
cout<<"exit"<<endl;
    return 0;
}
# Q . 5  By this question we understand daimond  problem virtual concept 

#include<iostream>
using namespace std;
class dada{
protected :
int age ;
public :
void set_age(int a ){
    age = a;

}
//void get_age(void ){
//cout<<"dadaji age is "<<age<<endl;
//}
};
class beta : virtual public dada {
protected:
int age ;
public:
void set2_age(int a ){
    age = a;
}
//void get2_age(void){
//    cout<<" beta age "<<age<<endl;
//
//}

};
class beti : virtual public dada{
protected :
int age ;
public :
void set3_data(int a){
    age = a;
}
//void get3_data(void ){
//    cout<<"beti age "<<age<<endl;
//}
};
class nati : public beta ,public beti {
protected :
int age ;
public :
void set4_age(int a){
    age = a;
  //  get_age();
  //  get2_age();
  //  get3_data();
}
void display (void ){
    cout<<"age of virtual dada "<<dada :: age<<endl;
    cout<<"age of beta "<<beta :: age<<endl;
    cout<<"age of beti "<<beti :: age<<endl;
    cout<<"age of nati "<<nati :: age<<endl;

}
};

int main(){
    nati yade ;
    yade.set_age(89);
    yade.set2_age(32);
    yade.set3_data(33);
    yade.set4_age(12);
    yade.display();

    return 0;
}
# Q . 5 In this question we use simplecalculator operation and scintific_calculator operation 
#include<iostream>
#include<cmath>
using namespace std;
class simplecalculator {
 protected :
int suma;
int sumb;
public:
void set_data(int aa,int bb){
   suma  = aa;
   sumb = bb;
}
void get_data(){
    cout<<"value of suma is "<<suma<<endl;
    cout<<"value of sumb is "<<sumb<<endl;



}
  };
class scintific_calculator{

protected :
float  adda;
float  addb;
float addc;
public:
void setkaro(float  a,float b,){
    adda = a;
    addb = b;
    addc = sin(( a + b)*180.0/M_PI)// isko dhyan ma rakkho ki 
    // c++ ma hamesha value radian ma calc hoti hai 
    // degree ma convert karna ka liya ( 180.0/M_PI )
    
}
void getkaro(){
    cout<<"your first value "<<adda<<endl;
    cout<<"your second number "<<addb<<endl;
    cout<<"your second number "<<addc<<endl;


}
};
class hybridesolve : public simplecalculator, public scintific_calculator {
public :
void show(){
    cout<<"sum of suma and sumb "<<suma+sumb<<endl;
    cout<<"add two no refrence from calc "<< addc<<endl;
}


};



int main(){
hybridesolve run;
run.set_data(4,5);
run.setkaro(30.0,60.0);
run.show();

    return 0;
}
# Q . 6  In this question we understand how to use construction in multiple inheritence 
#include<iostream>
#include<string>
using namespace std;
class stationaryshop_old{
string  book1;
public :
stationaryshop_old(string   a){
    book1 = a;
cout<<"kitabo ki duniya "<<endl;
}
set_book_name(void ){
    cout<<" book name "<<book1<<endl;

}


};
class stationaryshop_new{
string  book2;
public :
stationaryshop_new(string  a)
{
    book2 = a;
   
}
setkaro_book_name(void){
    cout<<"book name "<<book2<<endl;
}
};
class kya_hai_woh : public stationaryshop_old ,public stationaryshop_new{
string  book3 , book4;
public :
kya_hai_woh( string a, string b , string c,string d ):stationaryshop_new(a),stationaryshop_old(b){
    book3 = c;
    book4 = d;
}
void dikha_bhi_do(void){
    cout<<" kitabo ki duniya ma pheli kitab "<<book1<<endl;
    cout<<" kitabo ki duniya ma dusri  kitab "<<book2<<endl;
    cout<<" kitabo ki duniya ma tisri kitab "<<book3<<endl;
    cout<<" kitabo ki duniya ma chauthi  kitab "<<book4<<endl;
}


};
int main(){
kya_hai_woh dekhtahu("kite_runner" ,"stationary_shop","fear_not_be_strong",
"rommeo_and_black_brother");
dekhtahu.dikha_bhi_do();

    return 0;
}
# Q . 7 Create a program where two values, a and b, are stored. The addresses of a and b should be stored and the cmath library should be used to find the sin, cos and tan value in degrees. When calling these values, the object should be run through a pointer. The function that is created should also be a constructor function, and everything should be organized using multiple inheritance. The values of a and b should be taken from two different classes.
#include<iostream>
#include<cmath>
using namespace std;
class boat {
protected :
int first;
int *p = &first;
public :
boat (int a )
{

*p = a;
cout<<"mera constructor run kare gya "<<endl;

}
};
class nauka{
int second;
int *q = &second ;
nauka(int b ){
*q = b ;
    cout<<"your second constructor also ready"<<endl;
}
double radiansToDegrees(double radians) { 
    return radians * 180 / M_PI; }

};
class caption : public boat , public nauka {
public :
caption (int a , int b  ):boat(a),nauka(b){
cout<<"find sin value "<<radiansToDegrees(sin(first +second)  )<<endl;
cout<<"find cos  value "<<radiansToDegrees(cos(first +second) )<<endl;
cout<<"find tan value "<<radiansToDegrees(tan(first +second) )<<endl;

} 


};
int main(){

caption *z = new caption(30,30);
    return 0;
}

# Q . 8  how to read and write  words in file  

#include<iostream>
#include<fstream>
#include<string>
using namespace std;


int main(){
  ofstream grass("arcuss.text",ios :: app);
  grass<<"iska uska kiska  \n";
  grass<<"moaquito travel in the garden  \n";
  grass.close();

  ifstream aag;
  string st,st2;
  aag.open("arcuss.text");
  if (!aag.is_open())// file ko directly open karo 
  {
    cout<<"file nhi khul rhi hai "<<endl;
    return 1;// iska matlab agr ya condition nhi apply hue toh next step ma chale jao
  }
  
  aag>>st>>st2;// iska matlab hai jo file ma value hai woh st aur st2 ma store ho jayegi 
  cout<<"kya likha hai bhwa "<<st<<st2<<endl;
 //while(aag.eof()==0){
 // getline(aag st);
 //   cout<<st<<endl;
 // }
  
     return 0;
}
// kya abb bhi mujha koe doubt hai isma 
/*
jaisa ki maina dekha ki ofstream ka use hota hai likhna ka liya 
aur agr overwrite nhi karna chahta toh mujha append mode ka istam karna chahhya 
open ka parameter ma , ios :: app iska matlab ki ya constant hai aur change nhi kare saktye 
______ios::app____ .
if kaam kaam hai read karna ka ek 
behtarin chz jo ki loop hai jiska madat sa mai sari line ko read kare 
*/
# Q. 9 What is the execution process of a vector in C++?
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;

int main(){
    vector <int > vectoo1;
    vector <int > vectoo2;
    vectoo1.push_back(23);
    vectoo1.push_back(12);
    vectoo1.push_back(75);
    for (int  i = 0; i < vectoo1.size(); i++)
    {
    cout<<"the number is live"<<vectoo1[i]<<endl;
    }
    if (vectoo1.empty())
    {
        cout<<"agr vector khali ho  toh "<<endl;
    }
    else{
        cout<<"agr vector khali na ho toh "<<endl;
    }
vectoo2.assign(vectoo1.begin(), vectoo1.end());
    for (int  i = 0; i < vectoo2.size(); i++)
    {
    cout<<"the number is live"<<vectoo2[i]<<endl;
    }
vectoo1.reserve(10);
swap(vectoo2[0] , vectoo2[1]);
for (int i = 0; i < vectoo2.size(); i++)
{
    cout<<"the element value is change during "<<vectoo2[i]<<endl;
}
sort(vectoo2.begin(), vectoo2.end());
for (int i = 0; i < vectoo2.size(); i++)
{
    cout<<"the element value is change during "<<vectoo2[i]<<endl;
}
reverse(vectoo2.begin(), vectoo2.end());
for (int i = 0; i < vectoo2.size(); i++)
{
    cout<<"the element value is change during "<<vectoo2[i]<<endl;
}
vectoo2.erase(vectoo2.begin()+2);
for (int i = 0; i < vectoo2.size(); i++)
{
    cout<<"the element value is change during "<<vectoo2[i]<<endl;
}
return 0;
}
