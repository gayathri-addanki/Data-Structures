# Data-Structures

This is Implementation of single linked list
This file Contains All operations done on single linked list

#code

class Node:
    def _init_(self, data):
        self.data = data
        self.next = None

class SinglyLinkedList:
    def _init_(self):
        self.head = None

    def create(self):
        n = int(input("Enter number of elements: "))
        for i in range(n):
            e = int(input("Enter element: "))
            new_node = Node(e)
            if self.head is None:
                self.head = new_node
            else:
                temp = self.head
                while temp.next:
                    temp = temp.next
                temp.next = new_node

    def display(self):
        if self.head is None:
            print("List is empty")
        else:
            temp = self.head
            result = []
            while temp:
                result.append(temp.data)
                temp = temp.next
            print("List:", result)

    def insert_beg(self):
        e = int(input("Enter element to be inserted: "))
        new_node = Node(e)
        new_node.next = self.head
        self.head = new_node

    def insert_end(self):
        e = int(input("Enter element to be inserted: "))
        new_node = Node(e)
        if self.head is None:
            self.head = new_node
        else:
            temp = self.head
            while temp.next:
                temp = temp.next
            temp.next = new_node

    def insert_pos(self):
        pos = int(input("Enter position: "))
        e = int(input("Enter element to be inserted: "))
        new_node = Node(e)
        if pos == 1:
            self.insert_beg()
        else:
            temp = self.head
            for i in range(1, pos - 1):
                if temp is None:
                    print("Position out of bounds")
                    return
                temp = temp.next
            new_node.next = temp.next
            temp.next = new_node

    def del_beg(self):
        if self.head is None:
            print("List is empty")
        else:
            self.head = self.head.next

    def del_end(self):
        if self.head is None:
            print("List is empty")
        else:
            temp = self.head
            if temp.next is None:
                self.head = None
            else:
                while temp.next.next:
                    temp = temp.next
                temp.next = None

    def del_pos(self):
        pos = int(input("Enter position to delete: "))
        if self.head is None:
            print("List is empty")
        elif pos == 1:
            self.del_beg()
        else:
            temp = self.head
            for i in range(1, pos - 1):
                if temp is None or temp.next is None:
                    print("Position out of bounds")
                    return
                temp = temp.next
            temp.next = temp.next.next

if _name_ == "_main_":
    sll = SinglyLinkedList()

    while True:
        print("Select choice:")
        print("1. Create")
        print("2. Display")
        print("3. Insert at beginning")
        print("4. Insert at end")
        print("5. Insert at position")
        print("6. Delete at beginning")
        print("7. Delete at end")
        print("8. Delete at position")
        choice = int(input())
        
        if choice == 1:
            sll.create()
        elif choice == 2:
            sll.display()
        elif choice == 3:
            sll.insert_beg()
        elif choice == 4:
            sll.insert_end()
        elif choice == 5:
            sll.insert_pos()
        elif choice == 6:
            sll.del_beg()
        elif choice == 7:
            sll.del_end()
        elif choice == 8:
            sll.del_pos()
        else:
            print("Invalid choice")
        
        print()
