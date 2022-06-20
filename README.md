# leetcode_Add_Two_Numbers
+ linklist형태의 숫자 더하기 하지만 주의 해야 할건 숫자를 거꾸로 돌려 계산해야함
-----
+ Example1
```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```
----
+ Example2
```
Input: l1 = [0], l2 = [0]
Output: [0]
```
----
+ Example3
```
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```
----
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        carry = 0 # 올림 저장하기
        dummy = ListNode() # 빈 링크노드 만들기
        curr = dummy # 빈 링크노드 지목
        while l1 or l2: # 만약 l1과l2값이 있다면 
            if l1 != None:
                carry += l1.val # carry에 저장
                l1 = l1.next # 저장 했으니 다음 꺼 지목 해놓기
            if l2 != None:
                carry += l2.val
                l2 = l2.next   
            curr.next = ListNode(carry % 10) # 현재 위치의 다음 꺼는 l1+l2더한 값에서 mod 10한 결과
            carry = 1 if carry>=10 else 0 # 만약 l1+l2 더한 값이10보다 크면 다음 숫자에다가 1을 더해야함
            curr = curr.next # 위에서 만든 다음 노드로 이동
        if carry != 0: # 맨 마지막 숫자에서 더한 값이 10보다 클떄
            curr.next = ListNode(carry) # 1을 앞에다가 더해줌
        return dummy.next # 거꾸로 출력
```
---
### Result
Runtime: 76 ms, faster than 81.81% of Python3 online submissions for Add Two Numbers.\
Memory Usage: 14.1 MB, less than 10.26% of Python3 online submissions for Add Two Numbers.
