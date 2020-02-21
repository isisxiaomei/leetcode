```js
// 节点
function dataNode(data){
    this.data = data;
    this.next = null;
}

// 链表类
function List(){
    this.head = new dataNode();
    this.size = 0;
}
List.prototype = {
    contructor: List,
    add: function(value){
        var tempNode = new dataNode(value);
        if(this.head.next == null){
            this.head.next = tempNode;
        }else {
            var p = this.head;
            while(p.next != null){
                p = p.next;
            }
            p.next = tempNode;
        }
    },
    /**
     * 在位置pos处插入节点值为value
     * 若成功则返回插入的值，若失败则返回null
     */
    insert: function (value, position){
        var p = this.head;
        var pre = this.head;
        var count = 0;
        var temp = new dataNode(value);
        if (position <= 0) return null;
        if (position > this.listLength()){
            while(p.next != null){
                p = p.next;
            }
            p.next = temp;
            return value;
        } else {
            while(p.next != null){
                if(count == position){
                    break;
                }
                pre = p;
                p = p.next;
                ++count;
            }
            pre.next = temp;
            temp.next = p;
            return value;
        }
        return null;
    },

    find: function(value){
        var tempNode = this.head;
        while(tempNode != null){
            if(tempNode.data == value){
                return tempNode;
            }
            tempNode = tempNode.next;
        }
        return null
    },
    remove: function(value){
        var pre = this.head;
        var p = this.head;
        while(p != null){
            if (p.data == value){
                pre.next = p.next;
                return value
            }
            pre = p;
            p = p.next;
        }
        return null;
    },
    // 链表反转
    reverse: function(){
        var temp = new dataNode();
        var pre = this.head.next;
        var p = pre.next
        pre.next = null;
        while(p.next != null){
            temp.next = p.next;
            p.next = pre;
            pre = p;
            p = temp.next;
        }
        p.next = pre;
        this.head.next = p;
    },
    // 链表长度
    listLength: function(){
        var temp = this.head.next;
        var count = 0;
        while(temp != null){
            ++count;
            temp = temp.next;
        }
        return count;
    },
    // 打印链表
    display: function(){
        var p = this.head.next;
        while(p != null){
            console.log(p.data);
            p = p.next;
        }
    }
}


var list = new List();
list.add(1);
list.add(2);
list.add(3);
list.add(4);
// list.display();
// list.remove(2);
// list.display();
list.reverse();
list.display();

```