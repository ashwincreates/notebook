Given a sorted dictionary of an alien language having N words and k starting alphabets of a standard dictionary. Find the order of characters in the alien language.
*E.g. dictionary =  {"baa","abcd","abca","cab","cad"}
Output = b d a c* 

```python
def alienDictionary(dictionary, n, k):
    adj = {i:[] for i in 'abcdefghijklmnopqrstuvwxyz'}
    indegree = {i:0 for i in 'abcdefghijklmnopqrstuvwxyz'}
    for index, word in enumerate(dictionary[:-2]):
        fst = word
        snd = dictionary[index + 1]
        for a, b in zip(fst, snd):
            if a != b:
                adj[a].append(b)
                indegree[b] += 1
                break
    q = [i for i in 'abcdefghijklmnopqrstuvwxyz'[:k] if indegree[i] == 0]
    ans = []
    while len(q) != 0:
        letter = q.pop(0)
        ans.append(letter) 
        for next in adj[letter]:
            indegree[next] -= 1
            if indegree[next] == 0:
                q.append(next)
    print(ans)
```