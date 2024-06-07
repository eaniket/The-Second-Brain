- Code for basic implementation of trie
  ```C++
  struct Node{
	  Node* links[26];
	  bool isEnd;

	  bool containsKey(char ch){
		  return (links[ch-'a'] != NULL);
	  }

	  void put(char ch, Node* node){
		  links[ch-'a'] = node;
	  }

	  Node* get(char ch){
		  return links[ch-'a'];
	  }

	  void setEnd(){
		  isEnd = true;
	  }
  };

  class Trie{
	  private:
		  Trie root;
	  public:
	  Trie(){
		  root = new Node();
		  root->isEnd = false;
	  }

	  void insert(string word){
		  Node* node = root;
		  for(int i=0;i<word.length();i++){
			  if(!node->containsKey(word[i])){
				  node->put(word[i], new Node());
			  }
			  node = node->get(word[i]);
		  }
		  node->isEnd = true;
	  }

	  //Modify this function for different functions like prefix search
	  bool search(string word){
		  Node* node = root;
		  for(int i=0;i<word.length();i++){
			  if(!node->containsKey(word[i])){
				  return false;
			  }
			  node = node->get(word[i]);
		  }
		  return true;
	  }
  };
```
