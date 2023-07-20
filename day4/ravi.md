#include <bits/stdc++.h>
using namespace std;
#define pb push_back
#define ll long long
#define vi vector<int>
#define vl vector<ll>
vi vv(100000, 0);
int main()
{

    int t;
    cin >> t;
    while (t--)
    {
        int n, m, h;
        cin >> n >> m >> h;
        vector<vector<int>> v(n);
        for (int i = 0; i < n; i++)
        {
            for (int j = 0; j < m; j++)
            {
                int inp;
                cin >> inp;
                v[i].pb(inp);
                // cout << " v : " << v[i][j] << " ";
            }
            // cout << endl;
            // if (v[i].size() > 1)
            sort(v[i].begin(), v[i].end());
            // for (int j = 0; j < m; j++)
            // {
            //     cout << v[i][j] << " ";
            // }
            // cout << endl;
        }
        vector<pair<pair<int, int>, int>> p;
        // cout << "a";
        for (int i = 0; i < n; i++)
        {
            // cout << "b";
            int s = 0, ss = 0;
            bool b = 1;
            int ii = i;
            if (i == 0)
                ii = n;
            for (int j = 0; j < m; j++)
            {
                // cout << "c";
                if (!b)
                    break;
                s += v[i][j];

                if (s <= h)
                    ss++;
                else
                {

                    p.pb({{ss, s - v[i][j]}, ii});
                    b = 0;
                    break;
                }
            }
            if (b)
                p.pb({{ss, s}, ii});
            // cout << " p : " << p[i].first;
        }
        //  cout << "d";
        sort(p.begin(), p.end());
        for (int i = 0; i < n; i++)
        {
            // cout << " p : " << p[i].second << " " << p[i].first.first << " " << p[i].first.second << endl;
            if (p[i].second == n)
            {
                // cout << "f";
                cout << n - i << endl;
            }
        }
        //  cout << "g";
    }
    return 0;
}
