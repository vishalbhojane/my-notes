```js
// Written inside linked list class
merge(otherList) {
  let otherHead = otherList.head;
  let dummy = { value: 0, next: null };
  let current = dummy;

  while (this.head !== null && otherHead !== null) {
    if (this.head.value < otherHead.value) {
      current.next = this.head;
      this.head = this.head.next;
    } else {
      current.next = otherHead;
      otherHead = otherHead.next;
    }
    current = current.next;
  }

  if (this.head !== null) {
    current.next = this.head;
  } else {
    current.next = otherHead;
    this.tail = otherList.tail;
  }

  this.head = dummy.next;
  this.length += otherList.length;
}

const list1 = new LinkedList(1);
list1.push(3);
list1.push(5);
const list2 = new LinkedList(2);
list2.push(4);
list2.push(6);

list1.merge(list2);
```
