# assignment-1
# Delete the elements in an linked list whose sum is equal to zero
class Node():
  def __init__(self,data):
     self.data = data
     self.next = None

class Linkedlist():
   def __init__(self):
     self.head = None
    
   def append(self,data):
     new_node = Node(data)
     h = self.head
     if self.head is None:
         self.head = new_node
         return
     else:
         while h.next!=None:
             h = h.next
         h.next = new_node

   def remove_zeros_from_linkedlist(self, head):
     stack = []
     curr = head
     list = []
     while (curr):
         if curr.data >= 0:
             stack.append(curr)
         else:
             temp = curr
             sum = temp.data
             flag = False
             while (len(stack) != 0):
                 temp2 = stack.pop()
                 sum += temp2.data
                 if sum == 0:
                     flag = True
                     list = []
                     break
                 elif sum > 0:
                     list.append(temp2)
             if not flag:
                 if len(list) > 0:
                     for i in range(len(list)):
                         stack.append(list.pop())
                 stack.append(temp)
         curr = curr.next
     return [i.data for i in stack]

if __name__ == "__main__":
 l = Linkedlist()

 l.append(4)
 l.append(6)
 l.append(-10)
 l.append(8)
 l.append(9)
 l.append(10)
 l.append(-19)
 l.append(10)
 l.append(-18)
 l.append(20)
 l.append(25)
 print(l.remove_zeros_from_linkedlist(l.head))

 # Reverse a linked list in groups of given size
 # Python program to reverse a linked list in groups of given size
class Node:
	def __init__(self, data):
		self.data = data
		self.next = None

# Reverses the linked list in groups of size k and returns the pointer to the new head node.


def reverse(head, k):
# If head is NULL or K is 1 then return head
	if not head or k == 1:
		return head
	dummy = Node(-1) # creating dummy node
	dummy.next = head
	# Initializing three points prev, curr, next
	prev = dummy
	curr = dummy
	next = dummy
	count = 0
	toLoop = 0
	i = 0

	# Calculating the length of linked list
	while curr:
		curr = curr.next
		count += 1

	# Iterating till next is not none
	while next:
		curr = prev.next # Curr position after every reversed group
		next = curr.next # Next will always next to curr
		# toLoop will set to count - 1 in case of remaining element
		toLoop = count > k and k or count - 1
		for i in range(1, toLoop):
				# 4 steps as discussed above
			curr.next = next.next
			next.next = prev.next
			prev.next = next
			next = curr.next
		# Setting prev to curr
		prev = curr
		# Update count
		count -= k

	# dummy -> next will be our new head for output linked list
	return dummy.next

# Function to print linked list


def printList(node):
	while node is not None:
		print(node.data, end=" ")
		node = node.next


# Created Linked list is 1->2->3->4->5->6->7->8->9
head = Node(1)
head.next = Node(2)
head.next.next = Node(3)
head.next.next.next = Node(4)
head.next.next.next.next = Node(5)
head.next.next.next.next.next = Node(6)
head.next.next.next.next.next.next = Node(7)
head.next.next.next.next.next.next.next = Node(8)
head.next.next.next.next.next.next.next.next = Node(9)

print("Given linked list")
printList(head)
head = reverse(head, 3)

print("\nReversed Linked list")
printList(head)

# Merge a linked list into another linked list at alternate positions.
# Python program to merge a linked list into another at alternate positions

class Node(object):
	def __init__(self, data:int):
		self.data = data
		self.next = None


class LinkedList(object):
	def __init__(self):
		self.head = None
		
	def push(self, new_data:int):
		new_node = Node(new_data)
		new_node.next = self.head
		# 4. Move the head to point to new Node
		self.head = new_node
		
	# Function to print linked list from the Head
	def printList(self):
		temp = self.head
		while temp != None:
			print(temp.data)
			temp = temp.next
			
	# Main function that inserts nodes of linked list q into p at alternate positions.
	# Since head of first list never changes
	# but head of second list/ may change,
	# we need single pointer for first list and double pointer for second list.
	def merge(self, p, q):
		p_curr = p.head
		q_curr = q.head

		# swap their positions until one finishes off
		while p_curr != None and q_curr != None:

			# Save next pointers
			p_next = p_curr.next
			q_next = q_curr.next

			# make q_curr as next of p_curr
			q_curr.next = p_next # change next pointer of q_curr
			p_curr.next = q_curr # change next pointer of p_curr

			# update current pointers for next iteration
			p_curr = p_next
			q_curr = q_next
			q.head = q_curr



# Driver program to test above functions
llist1 = LinkedList()
llist2 = LinkedList()

# Creating LLs

# 1.
llist1.push(3)
llist1.push(2)
llist1.push(1)
llist1.push(0)

# 2.
for i in range(8, 3, -1):
	llist2.push(i)

print("First Linked List:")
llist1.printList()

print("Second Linked List:")
llist2.printList()

# Merging the LLs
llist1.merge(p=llist1, q=llist2)

print("Modified first linked list:")
llist1.printList()

print("Modified second linked list:")
llist2.printList()

# In an array, Count Pairs with given sum
# Python3 implementation of simple method to find count of pairs with given sum.

# Returns number of pairs in arr[0..n-1] with sum equal to 'sum'


def getPairsCount(arr, n, sum):

	count = 0 # Initialize result

	# Consider all possible pairs
	# and check their sums
	for i in range(0, n):
		for j in range(i + 1, n):
			if arr[i] + arr[j] == sum:
				count += 1

	return count


# Driver function
arr = [1, 5, 7, -1, 5]
n = len(arr)
sum = 6
print("Count of pairs is",
	getPairsCount(arr, n, sum))

# Find duplicates in an array

# Python3 code to find duplicates in O(n) time
numRay = [0, 4, 3, 2, 7, 8, 2, 3, 1]
arr_size = len(numRay)
for i in range(arr_size):

	x = numRay[i] % arr_size
	numRay[x] = numRay[x] + arr_size

print("The repeating elements are : ")
for i in range(arr_size):
	if (numRay[i] >= arr_size*2):
		print(i, " ")

# Find the Kth largest and Kth smallest number in an array
# Python3 program to find K'th smallest element

# Function to return K'th smallest element in a given array


def kthSmallest(arr, N, K):

	# Sort the given array
	arr.sort()

	# Return k'th element in the
	# sorted array
	return arr[K-1]


# Driver code
if __name__ == '__main__':
	arr = [12, 3, 5, 7, 19]
	N = len(arr)
	K = 2

	# Function call
	print("K'th smallest element is",
		kthSmallest(arr, N, K))

# Move all the negative elements to one side of the array
# Python code for the same approach
def move(arr):
arr.sort()

# driver code
arr = [ -1, 2, -3, 4, 5, 6, -7, 8, 9 ]
move(arr)
for e in arr:
	print(e , end = " ")

# Reverse a string using a stack data structure
# Python program to reverse a string using stack
# Function to create an empty stack.
# It initializes size of stack as 0


def createStack():
	stack = []
	return stack

# Function to determine the size of the stack


def size(stack):
	return len(stack)

# Stack is empty if the size is 0


def isEmpty(stack):
	if size(stack) == 0:
		return true

# Function to add an item to stack. It increases size by 1


def push(stack, item):
	stack.append(item)

# Function to remove an item from stack. It decreases size by 1


def pop(stack):
	if isEmpty(stack):
		return
	return stack.pop()

# A stack based function to reverse a string

def reverse(string):
	n = len(string)

	# Create a empty stack
	stack = createStack()

	# Push all characters of string to stack
	for i in range(0, n, 1):
		push(stack, string[i])

	# Making the string empty since all
	# characters are saved in stack
	string = ""

	# Pop all characters of string and
	# put them back to string
	for i in range(0, n, 1):
		string += pop(stack)

	return string

# Driver program to test above functions
string = "GeeksQuiz"
string = reverse(string)
print("Reversed string is " + string)

# Evaluate a postfix expression using stack
# Python program to evaluate value of a postfix expression


# Class to convert the expression
class Evaluate:

	# Constructor to initialize the class variables
	def __init__(self, capacity):
		self.top = -1
		self.capacity = capacity
		
		# This array is used a stack
		self.array = []

	# Check if the stack is empty
	def isEmpty(self):
		return True if self.top == -1 else False

	# Return the value of the top of the stack
	def peek(self):
		return self.array[-1]

	# Pop the element from the stack
	def pop(self):
		if not self.isEmpty():
			self.top -= 1
			return self.array.pop()
		else:
			return "$"

	# Push the element to the stack
	def push(self, op):
		self.top += 1
		self.array.append(op)

	# The main function that converts given infix expression
	# to postfix expression
	def evaluatePostfix(self, exp):

		# Iterate over the expression for conversion
		for i in exp:

			# If the scanned character is an operand
			# (number here) push it to the stack
			if i.isdigit():
				self.push(i)

			# If the scanned character is an operator,
			# pop two elements from stack and apply it.
			else:
				val1 = self.pop()
				val2 = self.pop()
				self.push(str(eval(val2 + i + val1)))

		return int(self.pop())



# Driver code
if __name__ == '__main__':
	exp = "231*+9-"
	obj = Evaluate(len(exp))
	
	# Function call
	print("postfix evaluation: %d" % (obj.evaluatePostfix(exp)))

	
# Implement a queue using the stack data structure
# Python3 program to implement Queue using two stacks with costly enQueue()

class Queue:
	def __init__(self):
		self.s1 = []
		self.s2 = []

	def enQueue(self, x):
		
		# Move all elements from s1 to s2
		while len(self.s1) != 0:
			self.s2.append(self.s1[-1])
			self.s1.pop()

		# Push item into self.s1
		self.s1.append(x)

		# Push everything back to s1
		while len(self.s2) != 0:
			self.s1.append(self.s2[-1])
			self.s2.pop()

	# Dequeue an item from the queue
	def deQueue(self):
		
			# if first stack is empty
		if len(self.s1) == 0:
			return -1;
	
		# Return top of self.s1
		x = self.s1[-1]
		self.s1.pop()
		return x

# Driver code
if __name__ == '__main__':
	q = Queue()
	q.enQueue(1)
	q.enQueue(2)
	q.enQueue(3)

	print(q.deQueue())
	print(q.deQueue())
	print(q.deQueue())









