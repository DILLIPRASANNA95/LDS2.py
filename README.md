Delete the elements in an linked list whose sum is equal to zero
class Node:
    def __init__(self, data=None):
        self.data = data
        self.next = None


def delete_zero_sum_nodes(head):
    if not head:
        return head

    dummy = Node(0)
    dummy.next = head
    current = dummy

    running_sum = 0
    sum_dict = {}

    while current:
        running_sum += current.data
        if running_sum in sum_dict:
            prev = sum_dict[running_sum]
            prev.next = current.next
        else:
            sum_dict[running_sum] = current
        current = current.next

    return dummy.next

head = Node(3)
head.next = Node(2)
head.next.next = Node(-1)
head.next.next.next = Node(1)
head.next.next.next.next = Node(-2)
head.next.next.next.next.next = Node(4)
print("Original Linked List:")
current = head
while current:
    print(current.data, end=" -> ")
    current = current.next
print("None")

head = delete_zero_sum_nodes(head)

print("Modified Linked List:")
current = head
while current:
    print(current.data, end=" -> ")
    current = current.next
print("None")

