---
ogImage: true
---

# リストレンダリング

Vueでは `v-for` ディレクティブを使って配列に基づいて項目のリストをレンダリングできます。これは ToDoリストのようなデータの一覧表示に非常に便利です。

## `v-for` の基本

`v-for` ディレクティブでは、`item in items` という形式の特別な構文が必要になります。ここで、`items` は元のデータの配列を指し、`item` は反復処理の対象となっている配列要素のエイリアスを指します：

```vue
<li v-for="item in items" :key="item.id">
  {{ item.message }}
</li>
```

重要なポイント：
- `:key` 属性を指定することで、Vue に各ノードを一意に追跡するためのヒントを与えます
- `item in items` の形式で、配列の各要素を順番に処理します

## 現在の実装の課題

プレイグラウンドで ToDo データをテーブルで表示していますが、配列の1件目のデータ `todos[0]` のみを直接参照して表示しています：

```vue
<tr>
  <td>{{ todos[0].done }}</td>
  <td>{{ todos[0].title }}</td>
  <td>{{ todos[0].note }}</td>
  <td>{{ todos[0].dueDate }}</td>
</tr>
```

この方法では：
- 1件目のデータしか表示されない
- データが増えても自動で表示されない

## チャレンジ

現在の固定インデックス `[0]` による参照を `v-for` を使った動的なレンダリングに変更してください：

1. `<tbody>` 内の固定の `<tr>` 要素を `v-for` を使って書き換えます
2. `v-for="todo in todos"` を使って全ての ToDoアイテムを動的にレンダリングします  
3. 各項目に一意の `:key="todo.id"` 属性を指定します

::note
`key` 属性は、Vue に各ノードを一意に追跡するためのヒントを与え、既存の要素を再利用して並べ替えを適用できるようにする際に必要となります。
::

## 実装後の効果

`v-for` を実装すると：
- 配列内の全てのToDoアイテムが表示される
- データが追加・削除されても自動で表示が更新される
- より保守性の高いコードになる

もし行き詰まったら、以下のボタンをクリックして解答を見ることができます。

:ButtonShowSolution

`v-for` を使うことで動的なデータ表示がとても簡単になりましたね！