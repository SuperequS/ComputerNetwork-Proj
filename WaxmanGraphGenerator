//Super wang
//ErGraph
#include <iostream>
#include <cstdlib>
#include <vector>
#include <queue>
#include <list>
#include <ctime>
#include<cstring>
#include <fstream>
#define FACTOR 0.4
using namespace std;
class cGraph{
private:
    vector< list<int> > adjList; //邻接表
public:
    bool adjListGenerator(); //判断是否连接边
    void erGraphGenerator();
    bool BFS();
    void init(); //初始化 adjList
    void outputGraph();
};

bool cGraph::adjListGenerator(){
    float tmp; //tmp为0~1内随机float类型浮点数
    tmp = rand()%1001;
    tmp /= 1000;
    if(tmp < FACTOR) return 1;
    else return 0;
}

void cGraph::init(){
    list<int> tmpList;
    tmpList.clear();
    for(int i=0;i<100;i++){
            adjList.push_back(tmpList); //初始化adjList，放入100个空list
        }
}

void cGraph::erGraphGenerator(){
    for(int i=0;i<100;i++) adjList[i].clear();
    int count = 0;
    bool vertexVisited[101][101]; //标记访问节点
    memset(vertexVisited,0,sizeof(vertexVisited));
    while(count<300){
            int x=rand()%100,y=rand()%100; //生成图的边随机产生
            if(adjListGenerator() && vertexVisited[x][y] !=1){
                    vertexVisited[x][y]=1;
                    adjList[x].push_back(y); //双向边（无向图）
                    adjList[y].push_back(x);
                    count++;
            }
    }
}

bool cGraph::BFS(){
    queue< int> q;
    bool visited[100];
    memset(visited,0,sizeof(visited));
    int i = 0;
    int count = 0;
    q.push(i); //从0开始遍历
    visited[i] = 1;
    count++;
    while(!q.empty()){
            int tmp = q.front();
            q.pop();
            list<int>::iterator head,tail; //同层入队
            head = adjList[tmp].begin();
            tail = adjList[tmp].end();
            for(head;head != tail; head++){
                    if(visited[*head] == 0){
                        q.push(*head);
                        visited[*head] = 1;
                        count++;
                    }
            }
    }
    if(count == 100) return 1;
    else return 0;
}

void cGraph::outputGraph(){
    ofstream fout;
    fout.open("ErGraph.txt");
    int count=0;
    for(int i=0;i<100;i++){
            list<int>::iterator iter;
            //cout<<i; //头节点
            fout<<i;
            for(iter=adjList[i].begin();iter!=adjList[i].end();iter++){
                fout<<"->"<<*iter; //邻接节点
                count++;
            }
            fout<<endl;
    }
    fout<<"Edge:"<<count/2<<endl;
    fout<<flush;
    fout.close();
}

cGraph graph;

int main( int argc, const char * argv[]){
    graph.init();
    srand((unsigned) time(0));
    do{
            graph.erGraphGenerator();
    }while(!graph.BFS());
    graph.outputGraph();
    return 0;
}
