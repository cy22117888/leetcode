208、实现Trie（前缀树）
===
实现一个 Trie (前缀树)，包含 insert, search, 和 startsWith 这三个操作。<br>

示例:<br>
```
Trie trie = new Trie();

trie.insert("apple");
trie.search("apple");   // 返回 true
trie.search("app");     // 返回 false
trie.startsWith("app"); // 返回 true
trie.insert("app");   
trie.search("app");     // 返回 true
```
说明:<br>
* 你可以假设所有的输入都是由小写字母 a-z 构成的。
* 保证所有输入均为非空字符串。

``
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/implement-trie-prefix-tree
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
``

```
class Trie {

    private TrieNode root;

    /** Initialize your data structure here. */
    public Trie() {
        root = new TrieNode();
    }
    
    /** 插入一个单词 */
    public void insert(String word) {
        TrieNode node = root;
        for (int i = 0; i < word.length(); ++i) {
            char currentChar = word.charAt(i);
            if (!node.containsKey(currentChar)) 
                node.put(currentChar, new TrieNode());
            node = node.get(currentChar);
        }
        node.setBoolEnd();
    }
    
    /** 查找一个单词 */
    public boolean search(String word) {
        TrieNode node = serchPrefix(word);
        return node != null && node.getBoolEnd();
    }
    
    /** 查找一个前缀 */
    public boolean startsWith(String prefix) {
        return serchPrefix(prefix) != null;
    }

    // 定义查找方法
    public TrieNode serchPrefix(String prefix) {
        TrieNode node = root;
        for (int i = 0; i < prefix.length(); ++i) {
            char currentChar = prefix.charAt(i);
            if (node.containsKey(currentChar))
                node = node.get(currentChar);
            else
                return null;
        }

        return node;
    }

    // 局部内部类
    class TrieNode {
        
        private TrieNode[] links;  // 存储字符节点

        private boolean boolEnd;  // 判断是否为叶子节点

        private final int size = 26;  // 定义字符节点总数（当前为26个小写字母）

        public TrieNode() {
            links = new TrieNode[size];
        }

        public boolean containsKey(char ch) {
            return links[ch - 'a'] != null; 
        }

        public TrieNode get(char ch) {
            return links[ch - 'a'];
        }

        public void put(char ch, TrieNode node) {
            links[ch - 'a'] = node;
        } 

        public boolean getBoolEnd() {
            return boolEnd;
        }

        public void setBoolEnd() {
            boolEnd = true;
        }
    }
}

/**
 * Your Trie object will be instantiated and called as such:
 * Trie obj = new Trie();
 * obj.insert(word);
 * boolean param_2 = obj.search(word);
 * boolean param_3 = obj.startsWith(prefix);
 */
```
