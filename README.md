# XMLParcer
# Description
Simple XML parcer
Takes file path (such as fstream uses) and gives tree.

Each node represents an XML Element and it has:
1) Name of element (name of tag)
2) Value of element (everything that written between open and close tags)
3) Map of attributes (name - value)
4) It's childrens

After parcing, file will have root node, that represents a file.
Also function returns 0, if something wrong happened, and 1, if everything went good. (it may return 1 even if something went bad, because it's hard to provide everything).

# Usage
## Open
### test.xml
```xml
<tag>
 <!-- sample -->
 <word value="Hello" size="9px"/>
 <sentence size = "10px"> 
  Hello,
    <color value = "#333333" >
      World
    </color>
 </sentence>
</tag>
```
### main.cpp
```C++
#include "XML.h"

int main() {
  XML::File f;
  f.open("test.xml");
  std::cout << f.root->children[1]->name << std::endl;
  std::system("pause");
  return 0;
}
```
This code will output

    sentence
    
## Save (or output)
### main.cpp
```C++
#include "XML.h"

int main() {
  XML::File f;
  f.open("test.xml");
  std::string s;
  f.save(std::cout);
  f.save("test2.xml");
  std::system("pause");
  return 0;
}
```
This code will output (both in file and cout)

    <tag>
     <word size="9px" value="Hello">
     </word>
     <sentence size="10px">
      Hello, 
      <color value="#333333">
       World 
      </color>
     </sentence>
    </tag>

