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
# Q . 2 "How to add values returned by functions from two separate classes?"
 
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

