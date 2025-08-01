---
ogImage: true
---

# 条件付きレンダリング

Vueでは `v-if` ディレクティブを使って、ブロックを条件に応じてレンダリングできます。ブロックは、ディレクティブの式が真を返す場合のみレンダリングされます。

## `v-if` の基本

`v-if` ディレクティブは、指定した式が真の場合のみ要素をレンダリングします。`v-else` は `v-if` に対する "else block" を示すために使用できます：

```vue
<button v-if="todo.done" type="button">
  <img src="@/assets/check-circle-green.svg" alt="完了" />
</button>
<button v-else type="button">
  <img src="@/assets/check-circle-gray.svg" alt="未完了" />
</button>
```

重要なポイント：
- `v-else` 要素は、`v-if` 要素の直後になければなりません
- 条件の式が真の場合のみ、該当する要素がレンダリングされます

## 現在の実装の課題

プレイグラウンドでは、ToDoリストの「完了」欄にボタンとアイコンを表示する部分で、まだ条件分岐ができていません：

```vue
<td class="text-center">
  <!-- ここに v-if/v-else でアイコンを切り替える処理を追加 -->
  {{ todo.done }}
</td>
```

現在は固定のテキストが表示されているだけで、ToDoの完了状態に応じたアイコンの切り替えができていません。

## チャレンジ

`<td class="text-center">` 内に `v-if` と `v-else` を使って、完了状態（`todo.done`）に応じて異なるボタンとアイコンを表示してください：

1. `todo.done` が `true` の場合：緑色のチェック付きアイコンを含むボタンを表示
2. `todo.done` が `false` の場合：グレーの丸いアイコンを含むボタンを表示
3. 各ボタンには適切な `alt` 属性を設定してアクセシビリティを向上させます

参考実装：
```vue
<button v-if="todo.done" type="button" class="button-icon">
  <img src="@/assets/check-circle-green.svg" alt="完了" />
</button>
<button v-else type="button" class="button-icon">
  <img src="@/assets/check-circle-gray.svg" alt="未完了" />
</button>
```

::note
`v-else` 要素は、`v-if` 要素の直後になければなりません。それ以外の場合は認識されません。
::

## 実装後の効果

`v-if` と `v-else` を実装すると：
- 各ToDoの完了状態に応じてアイコンが切り替わります
- 条件付きレンダリングの基本概念が理解できます
- より動的で視覚的に分かりやすいUIになります

もし行き詰まったら、以下のボタンをクリックして解答を見ることができます。

:ButtonShowSolution

`v-if` と `v-else` を使うことで、状態に応じた柔軟なUIが実現できます！
