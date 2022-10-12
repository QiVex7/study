    #include<bits/stdc++.h>
	using namespace std;
	int n,ans=0;
	int m[20];
	int s[20][20]={0};
	int a[20]={0},b[20]={0},c[20]={0};
	void print()
	{
		for(int i=1;i<=n;i++)
		{
			cout<<m[i]<<" ";
		} 
		cout<<endl;
	}
	int dfs(int x)
	{
		if(x>n)
		{
			ans++;
			if(ans<=3)
			{
				print();
			}
		}
		else
		for(int i=1;i<=n;i++)
		{
			if(s[x][i]==0&&a[i]==0&&b[i-x+7]==0&&c[i+x]==0)
			{
				s[x][i]=1;
				a[i]=1;
				b[i-x+7]=1;
				c[i+x]=1;
				m[x]=i;
				dfs(x+1);
				s[x][i]=0;
				a[i]=0;
				b[i-x+7]=0;
				c[i+x]=0;
				m[x]=0;
			}
		}
	}
	int main()
	{
	//	freopen("nqueen.in","r",stdin);
	//	freopen("nqueen.out","w",stdout);
		cin>>n;
		dfs(1);
		cout<<ans;
	//	fclose(stdin);fclose(stdout);
	}