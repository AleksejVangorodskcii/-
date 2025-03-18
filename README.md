# -def reverse_string_main(s):
    if len(s) == 0:
        return ""
    return s[-1] + reverse_string_main(s[:-1])

def reverse_string_tail(s, acc=""):
    if len(s) == 0:
        return acc
    return reverse_string_tail(s[:-1], acc + s[-1])

# 2. Рекурсивне переставлення сусідніх елементів у зв'язаному списку

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def swap_pairs_main(head):
    if not head or not head.next:
        return head
    new_head = head.next
    head.next = swap_pairs_main(new_head.next)
    new_head.next = head
    return new_head

def swap_pairs_tail(head, prev=None):
    if not head or not head.next:
        return prev if prev else head
    new_head = head.next
    head.next = new_head.next
    new_head.next = head
    return swap_pairs_tail(head.next, new_head)

# 3. Числа Фібоначчі

def fibonacci_main(n):
    if n <= 1:
        return n
    return fibonacci_main(n - 1) + fibonacci_main(n - 2)

def fibonacci_tail(n, a=0, b=1):
    if n == 0:
        return a
    if n == 1:
        return b
    return fibonacci_tail(n - 1, b, a + b)

# 4. Кількість шляхів до вершини

def climb_stairs_main(n):
    if n <= 2:
        return n
    return climb_stairs_main(n - 1) + climb_stairs_main(n - 2)

def climb_stairs_tail(n, a=1, b=2):
    if n == 1:
        return a
    if n == 2:
        return b
    return climb_stairs_tail(n - 1, b, a + b)

# 5. Реалізація функції pow(x, n)

def power_main(x, n):
    if n == 0:
        return 1
    if n < 0:
        return 1 / power_main(x, -n)
    return x * power_main(x, n - 1)

def power_tail(x, n, acc=1):
    if n == 0:
        return acc
    if n < 0:
        return power_tail(x, n + 1, acc / x)
    return power_tail(x, n - 1, acc * x)
