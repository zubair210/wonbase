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
