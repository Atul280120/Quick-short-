# Quick-short-
quick short in CPP user input
#include <bits/stdc++.h>
using namespace std;
int partion(vector<int>& v,int s,int e)
{
    int count=0,pivot=v[s];
    for(int i=s+1;i<=e;i++){
        if(v[i]<=pivot){
             count++;
        }
    }
    int indexofpivot=s+count;
    swap(v[indexofpivot],v[s]);

    int i=s,j=e;
    while(i<indexofpivot && j>indexofpivot){
        while(v[i]<=pivot){
            i++;
        }
        while(v[j]>pivot){
            j--;
        }
        if(i<indexofpivot && j>indexofpivot){
            swap(v[i++],v[j--]);
        }
    
    }
    return indexofpivot;

}
vector<int> quickshort(vector<int>& v,int start,int end){
    // base case
     if(start>=end){
        return v;
     }
     // partion
    int p=partion(v,start,end);
    quickshort(v,start,p-1);
    quickshort(v,p+1,end); 
    return v;
}
int main(){ 
  int n;
  cin>>n;
  vector<int>m;
  for(int i=0;i<n;i++){
    int temp;
    cin>>temp;
    m.push_back(temp);
  }
  quickshort(m,0,n-1);
  for(int i=0;i<n;i++){
    cout<<m[i]<<" ";
  }
 return 0;
}
