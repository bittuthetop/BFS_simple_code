# BFS_simple_code
BFS simple complete code
#include<iostream>
#include<vector>
#include<list>
#include<unordered_map>
#include<queue>
using namespace std;
void bfs(unordered_map<int,bool>&visited,
 unordered_map<int,vector<int> >&adj, vector<int>&ans 
 ,int node,int vertex){
    queue<int>q;
    q.push(node);
    visited[node] = 1;
    while(!q.empty()){
        int frontnode = q.front();
        q.pop();
        ans.push_back(frontnode);
       for(auto i:adj[frontnode]){
          if(visited[i]==0){
            q.push(i);
            visited[i] = 1;
          }
       }
    }
}
int main(){
       int vertex;
    cout << "Enter the number of vertices: ";
    cin >> vertex;
    vector<pair<int, int> > edges;
     int e;
    cout<<"enter the total edges"<<endl;
    cin>>e;
    for (int i = 0; i < e; i++) {
        int p, q;
        cin >> p >> q;
        edges.push_back(make_pair(p, q));
    }
    
   unordered_map<int,vector<int> >adj;
    for(int i =0;i<vertex;i++){
        int u = edges[i].first;
        int v = edges[i].second;
        adj[u].push_back(v);
        adj[v].push_back(u);
    }

    vector<int>ans;
    unordered_map<int,bool>visited;

    for(int i =0;i<vertex;i++){
        if(visited[i]==0){
           bfs(visited,adj,ans,i,vertex);
        }
    }
    for(int i =0;i<ans.size();i++){
        cout<<ans[i]<<" ";

    }cout<<endl;

    return 0;
}
