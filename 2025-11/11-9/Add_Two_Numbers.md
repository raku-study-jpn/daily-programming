# 【Daily Code DAY.1】Linked List（連結リスト）って何なの？

今日のテーマは**Linked List（連結リスト）**です。
「通常のリスト（list）と何が違うの？」
こんな疑問が湧きますが、一緒に見ていきましょう。

## Linked Listとは？

Python入門書で最初に登場する**リスト（list）**は、
複数のデータをメモリ上で連続して管理するデータ構造です。

イメージとしては「アドレス帳にデータが順番に並んでいる」感じです。
そのため、インデックス（番号）を使えば一瞬で目的のデータにアクセスできます。
一方で、途中に新しいデータを挿入する際には、
後ろのデータをすべてずらす必要があります。

![リストのイメージ](images\image_1.png)

これに対して**Linked List（連結リスト）**は少し仕組みが異なります。
データ（ノード）がそれぞれバラバラの場所（メモリアドレス）にあり、
各ノードが「次のノードはどこか」をポインタ（参照）として記憶しています。

そのため、
新しいデータを途中に挿入するときは「つなぎ方（next）」を少し変えるだけ。
つまり、挿入・削除がとても効率的に行えます。

ただし、欠点もあります。
「n番目のデータを取りたい」ときは、
最初から順番にたどるしかないのです。

![Linked Listのイメージ](images\image_2.png)

## Add Two Numbers問題（LeetCodeより）

プログラミング学習プラットフォームLeetCodeにLinked Listを使う問題があるので、一緒に見ていきましょう。
詳細はLeetCodeの[公式ページ](https://leetcode.com/problems/add-two-numbers/description/)をご確認下さい。

簡単に言うと、二つの非負整数が逆順でLinked List形式で格納されています。
それら二つを足し算した結果も逆順のLinked List形式で出力してください、といったものです。
回答の一例を示します。

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        dummy = ListNode(0)
        cur = dummy
        carry = 0

        while l1 or l2 or carry:
            x = l1.val if l1 else 0
            y = l2.val if l2 else 0
            total = x + y + carry

            carry = total // 10
            cur.next = ListNode(total % 10)
            cur = cur.next

            if l1:
                l1 = l1.next
            if l2:
                l2 = l2.next

        return dummy.next
```

Liked Listを定義するクラスとAdd Two Numbers問題を解くクラスを定義しています。
コード中にもありますが、ListCode.valで現在のListCodeのデータを確認し、
ListCode.nextで次のデータへ移動するイメージです。
リストと違い、Pythonに組み込まれているわけではないので、自身でListCodeクラスを定義して下さい。

今日はここまでです！
皆さんも美しいプログラミングライフを！

