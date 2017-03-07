---
layout: post
title:  "k-means clustering C implementation"
date:   2017-03-07 01:34:52 -0400
categories: jekyll update
---

#include <bits/stdc++.h>
#include <vector>
#include <utility>
#include <algorithm> 
int dist(std::pair<int,int>,std::pair<int,int>);
std::pair<int,int> centroid(std::vector< std::pair<int,int> >);
int main()
{
	printf("enter number of data items\n");
	int n;
	scanf("%d",&n);
	printf("enter number of clusters\n");
	int k;
	scanf("%d",&k);
	int x,y;
	std::vector< std::pair<int,int> > v;
	printf("Enter %d data items\n",n);
	for(int i=0;i<n;i++)
	{    
		scanf("%d",&x);
		scanf("%d",&y);
		v.push_back(std::make_pair(x,y));
	}
	for(int i=0;i<v.size();i++)
	{
		printf("%d ",v[i].first);
		printf("%d\n",v[i].second);
	}
    std::vector< std::pair<int,int> > cluster[100];
    //std::pair<int,int> cluster;
    std::vector<std::pair<int,int> > centroid_ci;
    for(int i=0;i<k;i++)
    {
    	centroid_ci.push_back(v[i]);
    }
   
      int cluster_vi[1000]={0};
     int d;
     int min=9999;
     int minindexcluster=0,currcluster=0;
     int change=1;
     int iterations=0;
     for(int i=0;i<n;i++)
     cluster[0].push_back(v[i]);
    while(change!=0||iterations<200)
    {	change=0;
    	for(int i=0;i<n;i++)
	    {min=9999;
	    	for(int j=0;j<k;j++)
	    	{
		    	d=dist(v[i],centroid_ci[j]);
		    	if(d<min)
		    	{
		    		min=d;
		    		minindexcluster=j;

		    	}
		    	
		    }
		    currcluster=cluster_vi[i];
		    if(minindexcluster!=currcluster)
		    	{	
		    		change=1;
		    		cluster[currcluster].erase(std::remove(cluster[currcluster].begin(), cluster[currcluster].end(), v[i]), cluster[currcluster].end());
	        		centroid_ci[currcluster]=centroid(cluster[currcluster]);
	        		cluster[minindexcluster].push_back(v[i]);
		   			centroid_ci[minindexcluster]=centroid(cluster[minindexcluster]);
		   			cluster_vi[i]=minindexcluster;
	    	    }
    	}
    	iterations++;
	}
	for(int i=0;i<k;i++)
	{
		printf("\ncluster%d: ",i+1);
		for(int j=0;j<cluster[i].size();j++)
			{	
				printf(" (%d",cluster[i][j].first);
				printf(",%d)",cluster[i][j].second);
			}
	}
}   
int dist(std::pair<int,int> a,std::pair<int,int> b)
{    int x1=a.first;
	int x2=b.first;
	int y1=a.second;
	int y2=b.second;
	return(int(sqrt(pow((x1-x2),2)+pow((y1-y2),2))));
}
std::pair<int,int> centroid(std::vector< std::pair<int,int> > v)
{
	int size=v.size();
	int sumx=0,sumy=0;
	 
	for(int i=0;i<size;i++)
	{
		sumx+=v[i].first;
		sumy+=v[i].second;
	}
		int a=(int)(sumx/size);
		int b=(int)(sumy/size);
	return(std::make_pair(a,b));
}
