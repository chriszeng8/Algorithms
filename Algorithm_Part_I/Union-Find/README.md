##Union-find
Chris Z. Zeng, Feb 14, 2015\
Notes from Coursera Class Algorithm Part I from Princeton University

####1.Quick-find 
Takeaways:
Quick-find takes $N^2$ array access to process sequence of $N$ union commands on $N$ objects.\
Quick-find is a quadratic algorithm, which is simply not scalable.

Steps:\
1. Set id of each object to itself\
2. Union operatr: U(p,q) update all entries whose id= id[p] to be id[q].

```
public class quickFind {
     private int [] id;

     /* Initialization: set id of each object to itself*/
	public void QuickFindUF (int N){
		id = new int [N];
		for(int i = 0; i< N; i++){
			id[i]=i;
		}
	}
     
     /* Connect operation: see if object p and q are connected*/
	public boolean connected(int p, int q){
		return id[p] == id[q];
	}

     /* Union operation: Update all entries whose id= id[p] to be id[q]*/
	public void union(int p, int q){
		int pid = id[p];
		int qid = id[q];
		for(int i =0; i<id.length; i++){
			if(id[i] == pid){
				id[i] = qid;
			}
		}
	}
}
```