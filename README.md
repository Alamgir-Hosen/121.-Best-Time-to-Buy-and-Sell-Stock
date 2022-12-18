# 121.-Best-Time-to-Buy-and-Sell-Stock and 122.
#include<bits/stdc++.h>
using namespace std;
int mprofit(vector<int>&v,int n)
{
    int profit;
    int mprofit=0;
    int minprofit=INT_MAX;
    for(int i=0;i<n;i++)
    {
        if(v[i]<minprofit)
        {
            minprofit=v[i];
        }
        else {
            profit=v[i]-minprofit;
            mprofit=max(mprofit,profit);
        }
        
    }
    return mprofit;
}
int mprofit1(vector<int>&v,int n)
{
    int maxp=0;
    for(int i=0;i<n;i++)
    {
        vector<int>segment1(v.begin()+0,v.begin()+i);
        vector<int>segment2(v.begin()+i,v.begin()+n);
       int n1=segment1.size();
       int n2=segment2.size();
        int p=mprofit(segment1,n1)+mprofit(segment2,n2);
       maxp=max(maxp,p);
    }
    return maxp;
}
int main()
{
    vector<int>v;
    int n,t;
    cin>>t;
    while(t--)
    {
        cin>>n;
        for(int i=0;i<n;i++)
        {
            int a;
            cin>>a;
            v.push_back(a);
        }
        cout<<mprofit1(v,n)<<endl;
    }
    return 0;
}
