###### Word ladder 1
Finding the shortest number of steps to reach end word from begin word

Here we simply start doing a BFS from begin word, and since at a time only one letter can differ we find all possible values and append it to the queue 
```python
def ladderLength(beginWord, endWord, wordList):
    wordSet = {word: False for word in wordList}
    if endWord not in wordSet:
        return 0
    queue = [beginWord]
    changes = 1
    while len(queue) > 0:
        size = len(queue)
        for _ in range(size):
            word = queue.pop(0)
            if word == endWord:
                return changes
            for i in range(len(word)):
                for j in range(0, 26):
                    newWord = word[:i] + chr(ord('a') + j) + word[i + 1:]
                    if newWord in wordSet and not wordSet[newWord]:
                        queue.append(newWord)
                        wordSet[newWord] = True
        changes += 1
    return 0
```

###### Word Ladder 2
Find all possible shortest paths, to reach end word from begin word

> [!warning] This solution gives TLE

Basically we do a BFS and keep a track of paths

```python
def findLadders(beginWord, endWord, wordList):
    wordMap = {beginWord: [[beginWord]]}
    wordSet = {word: False for word in wordList}
    queue = [beginWord]
    queueSet = {}
    wordSet[beginWord] = True
    res = []
    while len(queue) > 0:
        size = len(queue)
        newMap = {}
        for i in range(size):
            word = queue.pop(0)
            if word == endWord:
                res = wordMap[word]
                continue
            for i in range(len(word)):
                for c in 'abcdefghijklmnopqrtsuvwxyz':
                    newWord = word[:i] + c + word[i + 1:]
                    if newWord in wordSet and not wordSet[newWord]:
                        if newWord not in newMap:
                            newMap[newWord] = [path + [newWord] for path in wordMap[word]]
                        else:
                            newMap[newWord] += ([path + [newWord] for path in wordMap[word]])
                        if newWord not in queueSet:
                            queue.append(newWord)
                            queueSet[newWord] = True
        for word in queue:
            wordSet[word] = True
        queueSet = {}
        wordMap = newMap
    return res
```