# wonbase
this is my first repository.
<br>
Author - zubair (bhao)
# Q // do value ko dono value alag alag class ka hongi  iss  question ma dono value ko exchange karna hoga aur ya question run nhi kar rha hia isma kuch problem hia 

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
