//Super
//WaxmanGraph
#include <iostream>
#include <cstdlib>
#include <vector>
#include <queue>
#include <list>
#include <ctime>
#include<cstring>
#include <fstream>
#include<cmath>
#define ALPHA 2.55
using namespace std;
#define sqr(x) (x)*(x)

struct Node{
    int x,y;
}P[101];

class cGraph{
private:
    vector< list<int> > adjList;
public:
    bool adjListGenerator(double dist); //根据欧氏距离判断是否生成边
    void erGraphGenerator();
    bool BFS();
    void init();
    void outputGraph();
};

bool cGraph::adjListGenerator(double dist){
    float tmp;
    tmp = rand()%1001;
    tmp /= 1000;
    double p = ALPHA*exp(-dist/(5*sqrt(2))); //生成条件
    if(tmp < p) return 1;
    else return 0;
}

void cGraph::init(){
    list<int> tmp;
    tmp.clear();
    for(int i=0;i<100;i++){
            adjList.push_back(tmp);
    }
}

void cGraph::erGraphGenerator(){
    for(int i=0;i<100;i++)adjList[i].clear();
    int count = 0;
    for(int i=0;i<100;i++){
            P[i].x=rand()%101,P[i].y=rand()%101; //为所有节点随机生成坐标
    }
    for(int i=0;i<100;i++){
            int x1=P[i].x,y1=P[i].y;
            for(int j=i+1;j<100;j++){
                    int x2=P[j].x,y2=P[j].y;
                    double dist=sqrt(sqr(x1-x2)+sqr(y1-y2));
                    if(adjListGenerator(dist)){
                            adjList[i].push_back(j);
                            adjList[j].push_back(i);
                            }
                    }
            }
}

bool cGraph::BFS(){
    queue< int> q;
    bool visited[100];
    memset(visited,0,sizeof(visited));
    int i = 0;
    int count = 0;
    q.push(i);
    visited[i] = 1;
    count++;
    while(!q.empty()){
            int tmp = q.front();
            q.pop();
            list<int>::iterator head,tail;
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
    fout.open("WaxmanGraph.txt");
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
