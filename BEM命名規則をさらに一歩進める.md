[BEMIT: Taking the BEM Naming Convention a Step Further](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/?fbclid=IwAR05aekVmZVetB4Y8bNU3MFN602enezeaJ2MWWy6dGeu9YRKQbOEiRnDAk8)

私や私の仕事を長く追ってきた人なら誰でも、私がBEMの命名規則を大々的に支持していることを間違いなく知っているでしょう。

この記事でお話しするのは、BEMの代替や別の命名規則ではなく、BEMをレベルアップさせるための小さな追加です。

この拡張されたBEM構文は、(まだ発表されていませんが)逆三角形CSSアーキテクチャからいくつかのパラダイムとパターンを借用しているため、BEMITと呼ばれています。BEM + ITCSS = BEMIT です。

BEM について簡単に説明すると、BEM はコードベース内のすべてのクラスを 3 つのグループの 1 つに分解することで動作します。

- Block: コンポーネントの唯一の root
- Element: ブロックのコンポーネント部分
- Modifier: ブロックの変形または拡張

Blocks, Elements, and Modifiers: BEM.

プロジェクト内のすべてのクラスは必ずこれらのカテゴリのいずれかに当てはまります。

BEM のポイントは、マークアップの透明性を高め、より明確にすることです。BEM は、クラスがどのように相互に関連しているかを開発者に伝えます。

例えば、以下の HTML の塊の中のユーザー関連のクラスをすべて削除するように頼んだ場合、どのクラスを削除しますか？

