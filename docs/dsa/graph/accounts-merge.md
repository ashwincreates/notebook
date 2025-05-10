```python
def accountsMerge(self, accounts):
        n = len(accounts)
        email_map = {}
        acc = [i for i in range(n)]
        eml = [[] for i in range(n)]

        def find(v, parent):
            if parent[v] == v:
                return v
            p = find(parent[v], parent)
            parent[v] = p
            return p
            
        def union(u, v, parent):
            pu = find(u, parent)
            pv = find(v, parent)
            if pu == pv:
                return
            else:
                parent[pu] = pv

        for i, account in enumerate(accounts):
            name, *emails = account
            for email in emails:
                if email in email_map:
                    c = email_map[email]
                    union(i, c, acc)
                else:
                    email_map[email] = i
        
        for k, v in email_map.items():
            eml[find(v, acc)].append(k)

        ans = []
        for i in range(n):
            emails = eml[i]
            name = accounts[acc[i]][0]
            if len(emails) == 0:
                continue
            else:
                ans.append([name, *sorted(emails)])
        return ans
```