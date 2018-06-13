# Linked-list-even-odd-node-seperation
class node:

    def __init__(self,data):
        self.data=data
        self.next=None

class linked_list:

    def __init__(self):
        self.head=None


    def insert(self,new_data):

        new_node=node(new_data)
        temp=self.head

        while(temp!=None and temp.next!=None):
            temp=temp.next

        if(temp!=None):
            temp.next=new_node

        else:
            temp=new_node
            self.head=new_node

    def print_list(self):

        temp=self.head

        while(temp):

            print(temp.data)
            temp=temp.next


    def segregate(self):

        evenStart=None
        evenEnd=None
        oddStart=None
        oddEnd=None
        currentNode=self.head

        while(currentNode!=None):
            element=currentNode.data

            if(element%2==0):

                if(evenStart==None):
                    evenStart=currentNode
                    evenEnd=evenStart

                else:
                    evenEnd.next=currentNode
                    evenEnd=evenEnd.next

            else:

                if(oddStart==None):
                    oddStart=currentNode
                    oddEnd=oddStart

                else:
                    oddEnd.next=currentNode
                    oddEnd=oddEnd.next

            currentNode=currentNode.next

            if(oddStart==None or evenStart==None):
                return

            evenEnd.next=oddStart
            oddEnd.next=None
            self.head=evenStart
            

            t1=evenStart
            while(t1):
                print(t1.data)
                t1=t1.next
                


if(__name__=='__main__'):

    llist=linked_list()
    llist.insert(1)
    llist.insert(2)
    llist.insert(3)
    llist.insert(4)
    llist.insert(5)
    llist.insert(6)
    llist.insert(7)
    print("The linked list is given as:")
    llist.print_list()
    print("The segregated even and odd nodes linked list is:")
    llist.segregate()
    
    
    
