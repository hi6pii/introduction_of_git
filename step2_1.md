# 以下を参照して、特に記憶に残したい部分をコピペした
https://github.com/takanabe/introduction-to-git/blob/master/02_first_commit.md


### リポジトリの作成
    $ git init

### ディレクトリの確認
    $ ls -a


### 現在のリポジトリと作業コピーの状態を Git さんはどう認識しているか
    $ git status
「On branch master」 とありますね。「ブランチ master 上だよ」  
「Initial commit」 と書かれていますね。「最初のコミットだよ」と書かれています  
「Untracked files:」 。「トラックされていないファイルは以下のとおりだよ：nyan.txt」  
「use "git add <file> ..." to include in what will be committed」 と書かれています。「コミットされるものに含めたければ "git add <file>..." 使えば良いよ」ってことですね。  
「nothing added to commit but untracked files present (use "git add" to track)」 と書かれていますね。「コミットするものがなにもないよ、でも追跡されてないファイルがあるよ(追跡したければ "git add" するといいよ)」  


### stageとunstage

「次にコミットするときにリポジトリに反映される内容の置き場」のことを、"staging area" と呼んでいます
stage

    $ git add nyan.txt

unstage

    $ git rm --cached nyan.txt



### commitしてみる

    $ git commit

メッセージを書く意味  
1. 「履歴を残す」。「誰が」「いつ」「何をしたか」を、コミットメッセージとして残しておく必要がある -> 参照、再現、分岐
  1. 再現：動作しなくなる一つ手前に戻り作業をやり直すといったことや、バグが発生する時点の成果物を、他のメンバーに確認してもらう、といったことが可能になります
  1. 分岐：動作しなくなる手前の状態を元に別の変更を加えていき、それぞれのパターンをメンバーに評価してもらう、といったこともできるようになります
1. 作業の競合を防ぐ -> 統合(merge)が可能になり、他のメンバーと効率よく並行して作業をすすめられる


### 履歴を確認

    $ git log


### コミットされると何がおこるのか

コミットされたとり、リポジトリには新しい「コミットオブジェクト」が生まれる
コミットオブジェクトは「stagingされていたファイルの内容 + コミットメッセージ」
それぞれのコミットオブジェクトには一意のidがついている


### stageされたfileの変更

    $ git status
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
「コミット用に stage されてない変更は以下の通りです。変更されたファイル：nyan.txt」作業ディレクトリの内容を変更したけど、そのファイルのその内容が staging area に上がってないわけですね。  
「use "git checkout -- <file>..." to discard changes in working directory」だそうです。「"git checkout -- <file> ..." すると、作業ディレクトリ内での変更をなかったことにできるよ！」

    $ git add
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
括弧の中は「use "git reset HEAD <file>..." to unstage」とあります。「"git reset HEAD <file> ..." ってやるとunstageできるよ」ってことですね。

    $ git reset HEAD nyan.txt
    Unstaged changes after reset:
    M   nyan.txt
「unstageされた変更は以下の通りだよ。M nyan.txt」ってことですね。M nyan.txt はなんとなく察しがついてるかと思いますが、「Modified」の M です。nyan.txtが変更されてるけど、その変更が git reset によって unstage されたよって言ってくれてますね。


### コミットオブジェクトふたたび
    $ git commit
    1 file changed, 1 insertion(+), 1 deletion(-)
「一つのファイルが変更されててー、一行挿入されててー、一行消えてる！」とのことです、一行編集するってのは言い換えれば一行消して一行挿入するってことなので、なるほどね！って感じですね。

大事なのは：
- コミットには親子関係がある
- コミットオブジェクトには「親コミットはどれか」という情報と、「この瞬間のファイルの状態」という情報が入っている
- これらのふたつの情報を比べることによって、Git さんはいつでも「その 2 つのコミットの間にどのような変更が行われたか」を知ることができる


    $ git log --graph  


git log の表示フォーマットはいろいろいじれるので、気になるひとは調べてみて、自分の好きなフォーマットで見てみるといいと思います


### ファイルの削除
    $ git rm filename
git rm というコマンド：
- 作業ディレクトリにファイルが存在するときにはそのファイルを削除する(すでに無い場合はなにもしない)
- その後「ファイルを削除したよ」という情報を stage する


### ファイルのリネーム、移動
「ファイルのリネーム、移動」は、実質は「新しい場所(名前)に同じ内容のファイルを作って、古い場所にあるファイルを消す」という動作である。
なので、ファイルをリネーム/移動 した場合は、「新しくファイルができたよ」という情報を git add で stage、「古いファイルは消えたよ」という情報を git rm で stage することでリネーム/削除が表現できる。

    $ git add ＜リネーム後のファイルの名前＞
    $ git rm ＜リネーム前のファイルの名前＞

一方

      $　git mv  ＜リネーム前のファイルの名前＞ ＜リネーム後のファイルの名前＞

を使うと、「作業ディレクトリ内のファイルのリネーム/移動」と、「その変更を stage」を一気にやってくれる


### git におけるブランチはただのポインタである
ブランチというのはコミットオブジェクトを指し示す

    $ git branch

以下Tips:

    $ git log --graph --pretty=format:'%s %d'

git log --graph に --pretty=format:'%s %d' というオプションを渡してみました。これは、コミットの履歴を '%s %d' というフォーマットで表示してね、という意味です。'%s' はコミットメッセージ、'%d' がブランチを意味します。
ログを見て理解すべきことは「master というブランチが存在していて、その master ブランチが "動物ファイルを animals ディレクトリに移動" というコミットオブジェクトを指している」ということ。

    $ git log --graph --date-order --all --pretty=format:'%h %Cred%d %Cgreen%ad %Cblue%cn %Creset%s' --date=short

### 新しいブランチの作成
    $ git branch my_first_branch
my_first_branch というブランチが出来ていて、masterと同じく最新のコミットオブジェクトを指しているのが見て取れるとおもいます。

    $ git commit
コミットが行われると、コミットオブジェクトが作成されるのでしたね。そして、そのコミットオブジェクトは、「親コミットオブジェクトはどれなのか」という情報と、「その瞬間のファイルの状態」という情報を持っているのでした。そうです。実は、「親コミットオブジェクト」になるのは、「コミットするときに選択されていたブランチが指し示しているコミットオブジェクト」なのです。コミットが行われると、Git さんは「選択されているブランチが指し示しているコミットオブジェクト」を親として、新しいコミットオブジェクトを作成します。その後、Git さんは「選択されているブランチ」がこの新しくできたコミットオブジェクトを指し示すように更新します。

このタイミングで HEAD という存在のなぞにも答えておきましょう。実はこの HEAD というのは特殊なブランチ(ポインタ)で、「今選択しているブランチがどれなのか」という情報を保持しているのです。今、HEAD は master と同じところにありますね。つまり、今は master が選択されている、ということです。


### 選択中のブランチを切り替えてみる
    $ git checkout my_first_branch
あるブランチを checkout すると、Git さんはふたつのことを行います。
1. HEADを指定したブランチに切り替える
2. 作業ディレクトリの内容を、そのブランチが指し示すコミットのときの状態に復元する
履歴を残す能力によりできるみっつのことのうち、「参照」と「復元」を実際に行ってみました。残るは「分岐」です。


### マージする
    Merge made by the 'recursive' strategy.
     animals/mow.txt | 1 +
     1 file changed, 1 insertion(+)
     create mode 100644 animals/mow.txt

 「Merge made by the 'recursive' strategy.」 とありますね。「'recursive' strategy で merge されたよ」だそうです。'recursive' starategy ってなに……って感じですが、ひとまず今はそれは置いておきます。「なんらかの方法でマージされたんだな」と今は思っておいてください。

 その次の行、「animals/mow.txt | 1 +」と表示されています。なんとなくわかるでしょうか。「animals/mow.txtというファイルに1行増えてるよ」くらいの感じですね。その下に表示されている内容も、もうわかりますね。「1ファイル変更があって、1行追加されてるよ」と、「animals/mow.txt ってファイルを作ったよ」ですね。たしかに、my_first_branch にはあるけれど master にはないファイルは、「"mow" と 1 行書かれた書かれた animals/mow.txt」というファイルでした。そのファイルを取り込むのだから、このような結果になるのは納得ですね。

1. `$ git merge branch_name`  で、今選択されているブランチに branch_name という名前のブランチのコミット内容を取り込むことができる
2. マージするときには「マージコミット」という特殊なコミットが行われ、マージコミットのコミットオブジェクトは親をふたつ持つ
3. そのマージコミットが持つ「この瞬間のファイルの状態」は、ふたつの親が持っていた内容を合わせたものになる
4. `git branch -d branch_name` とすることで、branch_name という名前のブランチを消すことができる


### 編集作業はブランチで
ではここから、緊急の作業のためのブランチを切ってそこに移動しましょう。名前は hotfix にしましょうか。今までは

    $ git branch ブランチ名
    $ git checkout ブランチ名
とふたつのコマンドを打っていましたが、「ブランチを切ってそこに移動する」というのはじつは一発でできるコマンドがあります。今回はそちらを使いましょう。

    $ git checkout -b hotfix
これで、 hotfix という名前のブランチを作成し、そのブランチを選択したことになります。

    $ git merge hotfix
    merge message:
    Fast-forward
     cat_hater_said.txt | 2 +-
     cat_lover_said.txt | 2 +-
     2 files changed, 2 insertions(+), 2 deletions(-)
このグラフ、一本道で、「分岐」してませんね。さて、このとき、master ブランチが hotfix ブランチの変更内容を取り込もうと思った場合、一番楽な方法はなんでしょうか。単純に master ブランチを hotfix と同じところを指すようにしてしまえば、それで master ブランチに hotfix ブランチの変更内容を反映したのと同じことになりますね。そういうとき、賢い Git さんは「じゃあそれでええやん」という感じで単純に master のブランチを hotfix と同じところまで進めるのです。で、こういう merge の仕方を「Fast-forward」と呼んでいるのです。

fast-fowardするとログが残らないのでそれがいやな場合

    $ git merge --no-ff hotfix

こうすることで recusive strategy でマージされる
ところで、今回は Fast-fowarding せずにマージコミットを作る方式でマージを行いましたが、Fast-foward できるときは Fast-foward してしまうほうが好みであるというひともいます。このあたりは現在でも活発に宗教戦争が起こっているので、あなたの所属する組織やプロジェクトのやり方に合わせるといいでしょう。


### マージ　競合
    $ git checkout master
    $ git merge unify_styles
    Auto-merging cat_lover_said.txt
    CONFLICT (content): Merge conflict in cat_lover_said.txt
    Auto-merging cat_hater_said.txt
    CONFLICT (content): Merge conflict in cat_hater_said.txt
    Automatic merge failed; fix conflicts and then commit the result.

「Auto-merging cat_lover_said.txt」は「cat_lover_said.txt を 自動マージしてるよ」でいいですね。そのあと、「CONFLICT (content): Merge conflict in cat_lover_said.txt」と言われています。オッ、これは「競合」ですね。よく考えてみると、hotfix でも cat_lover_said.txt の一番最後の行を編集していますし、unify_styles でも一番最後の行を編集してしまっています。このため、Git さんは「お、これどっちの状態を真とすればいいんだ？」と混乱してしまって、自動でマージが行えなかったわけですね。　　

そして最後に、「Automatic merge failed; fix conflicts and then commit the result.」と書かれていますね。「自動マージに失敗しちゃった＞＜ 競合を直して、その結果をコミットしてね！」と言われています。言われたとおりにしましょう。

と、そのまえに、なにはともあれ status を確認。

    $ git status
    # On branch master
    # You have unmerged paths.
    #   (fix conflicts and run "git commit")
    #
    # Unmerged paths:
    #   (use "git add <file>..." to mark resolution)
    #
    #   both modified:      cat_hater_said.txt
    #   both modified:      cat_lover_said.txt
    #
    no changes added to commit (use "git add" and/or "git commit -a")
見た事無い表示ですね。

「マージされてないパスがあるよ(コンフリクトを修正して git commit してね)。」だそうです。この「パス」ってのは「ファイルパス」のことですね。ファイルのことだと思ってくれてかまいません。

その下には「マージされてないパスは以下の通りだよ(修正したよってマーク付けるためには git add <file> ...してね)。
- 両方で変更されているファイル：cat_hater_said.txt
- 両方で変更されているファイル:cat_lover_said.txt
とありますね。

cat_hater_said.txtを見てみると
途中に

    <<<<<<< HEAD
    猫好きな人間がいるのが不思議。
    =======
    >>>>>>> unify_styles
のような記載がある。これは、「どこが自動でマージできなかったか」を Git さんが教えてくれたのです。
<<<< HEAD から ======　までは HEADで編集された内容です。今回はHEADはmasterでしたね。  
一方 ===== から　>>>>> unify_stylesまでがunify_stylesに書かれていた内容。どうやらgit さんは、unify_stylesのほうは
どうなおしたら良いかわからなかったみたいですね。

これを手動で解決してしまおう。(でもマージ先のものを参照したい場合、どうしたら良いのでしょう？？）

git status で確認します。

    $ git status
    # On branch master
    # All conflicts fixed but you are still merging.
    #   (use "git commit" to conclude merge)
    #
    # Changes to be committed:
    #
    #   modified:   cat_hater_said.txt
    #   modified:   cat_lover_said.txt
    #
    お、表示が変わりましたね。

「All conflicts fixed but you are still merging.(use "git commit" to conclude merge)」とありますね。日本語にすれば「競合は全部解決したけど、まだマージ中だよ。(マージを完成させるには、git commit してね)」です。


### マージ＆競合 まとめ
- なにか作業を行うときはブランチを切ってから行うと、いつでも「その作業を行う前の状態」に戻れるので便利
- 「分岐」してないブランチをマージするときには Fast-foward という手法が取られる
- Fast-foward だと、マージコミットは作られず、たんにブランチが進められる
    - Fast-foward したくないときには --no-ff というオプションを付ける
- マージしたときに競合が発生した場合には、手動でマージする
    - ファイルを手動で修正
    - git add ＜修正したファイル＞として「競合を直したよ」と Git に伝える
    - 全部直したら git commit でマージコミットを完成させる

### 作業はトピックブランチで
「特定の目的の作業を行うためのブランチ」のことを、「トピックブランチ」とか「フィーチャーブランチ」と呼ぶことが多いです。あるトピックやある機能に特化したブランチ、くらいの意味ですね。

### トピックブランチで作業を再開、したいんだけど……
今はこの unify_styles ブランチでの作業を始めたのが hotfix が行われる前でしたが、仮に、もしこれが、hotfix が行われたあとに発生したタスクだったら、話はずいぶんシンプルになるのにな、と思いませんか？

じゃあ、そういうふうに歴史を改変しちゃえばいいんです。改変しちゃいましょう。

    $ git checkout unify_styles
    $ git rebase master
    First, rewinding head to replay your work on top of it...
    Applying: under updating of files: tentative commit

「まず、head を巻き戻すよ。これは、君がやったことを最初からリプレイするためだよ！」と言ってますね。そして、そのあとに、「適用中：under updating of files: tentative commit」とあります。
rebaseで行われているのは
1. unify_styles の各コミットで「どのような変更を行ったのか」を覚えておく
1. master (hotfix を merge したあとの状態) を checkoutする
1. そこから新しくまた unify_stylesブランチを切る
1. 覚えておいた「どのような変更を行ったのか」をイチから適用し直して行く。


### rebaseは、いつもうまくいくわけではない
たとえば以下のようなメッセージがでてくる
    When you have resolved this problem, run "git rebase --continue".
    If you prefer to skip this patch, run "git rebase --skip" instead.
    To check out the original branch and stop rebasing, run "git rebase --abort".
    問題を解決したら、"git rebase --continue".をしてね。
    この変更をスキップしちゃいたいなら、"git rebase --skip" だよ。
    もとのブランチを checkout してリベースをやめてしまいたいなら、"git rebase --abort" してね


### 「直前のコミットをやりなおす」という歴史改変方法
    $ git commit --amend

### merge を使うべきなのか rebase を使うべきなのか

さて、rebase を使うとグラフや履歴がすっきりするのはわかりました。では、こういうケースではいつでも rebase を使うべきなのでしょうか？ これも結構現在でも宗教戦争が活発に行われているトピックなので、あなたの所属する組織やプロジェクトのやり方に合わせるのが良いでしょう。

ちなみに、筆者は最近では rebase のような大掛かりな過去改変は「ダークサイド」であるという見解に与するものです。rebaseすると、Git さんが勝手に過去のコミットを書き換えてしまいます。これによって、「ちゃんと問題なく動いていたコミット」が「動かないコミット」になってしまう可能性がある、というのがその理由です。

もちろん、マージコミットでもそのようなことは起こるのですが、マージコミットの場合はその後のテストでかならずすぐに「動かないコミット」を作ってしまったことを確認できますが、リベースで出来上がったコミットをいちいち再度テストするのは現実的ではないですよね？


### みんなで使う
まずは今回のブランチの運用のポリシーを決めましょう。

まず、masterブランチですが、master ブランチにコミットするものは「リリースするもの」だけ、ということにしましょう。開発途中のものをコミットするのは、「development」というブランチにします。そして、作業は development からトピックブランチを切って行います。

言い方を変えると、なにか作業をするときには development ブランチから topic ブランチを切って行います。そして、その作業が終わったら、develop ブランチでそのトピックブランチを merge します。これを繰り返して、development ブランチの状態が「リリースできるもの」になったら、master ブランチから development ブランチを merge します。

それともうひとつ、すでにリリースしてしまったものに不具合が見つかったときにそれを緊急で修正しなければならないときには、master ブランチから hotfix ブランチを切って、ここで修正した内容を master ブランチに merge することにしましょう。これで、開発中のものを急いでリリースせずに、緊急の対応だけは先にリリース版に組み込みことができますね。

そして、この緊急対応が無事にリリースされたなら、hotfix が取り込まれた master ブランチを development にマージすることにしましょう。このように運用することで、開発版にも、リリース版での修正を反映することができます。


### みんなでさわるリポジトリの作成
    $ git clone --bare 複製元 複製される先
という感じで --bare を付けてリポジトリを複製すると、作業ディレクトリなしで、リポジトリだけを複製することができるのです。

「みんなで触るリポジトリ」で直接作業を行うことはないので、このリポジトリには作業ディレクトリは要らないですよね。なので、みんなで触るリポジトリを作るときには --bare 付きで複製しましょう。みんなで触るリポジトリをこういう「bare repository」で作るのには、実はもうひとつ理由があるのですが、それはまた改めて説明しましょう。ちなみに、bareリポジトリの名前は、最後に「.git」を付けるのが慣習となってます。

さて、これで無事に「みんなで触るリポジトリ」が出来上がりました。これをcloneして使う。（なんで？？）

### リモートリポジトリとは
「あのリポジトリにコミット内容を反映させたい」とか「あのリポジトリの変更内容を取得してきたい」というようなことをするためには、「あのリポジトリ」にあたるリポジトリを、「リモートリポジトリ」として登録しておかなければなりません。

逆の言い方をすると、手元のリポジトリのコミット内容を別のリポジトリに反映させたり、別のリポジトリのコミット内容を手元のリポジトリに反映したい場合には、「リモートリポジトリ」として、そのリポジトリを登録しておく必要がある、ということです。

ちなみに、git clone でリポジトリを手元に複製してきた場合、Git さんが勝手に clone 元のリポジトリを、「origin」という名前のリモートリポジトリとして登録してくれるのです。これで、cloneしてきたリポジトリからコミット内容を手元に取り込んだり、手元のリポジトリのコミット内容をcloneしてきたリポジトリに反映できますね！Git さんってば気が利く！

    $ git remote
    origin

はい、origin が表示されました。これはつまり、「リモートリポジトリとして origin というリポジトリが登録されているよ」ということです。

    $ git log --graph --date-order --all --pretty=format:'%h %Cred%d %Cgreen%ad %Cblue%cn %Creset%s'  --date=short
    * 7730680  (HEAD -> master, origin/master, origin/development, origin/HEAD) 2017-01-05 TAKASHI add cat_lover_said.txt
origin/master, origin/development, origin/HEAD というみっつのブランチがありますね。これらはそれぞれ、
- origin リモートリポジトリ(つまり clone 元)の master ブランチ
- origin リモートリポジトリの development ブランチ
- origin リモートリポジトリのHEAD

を表しています。git clone をすると、クローン元に存在するコミットとブランチを、手元に複製してきます。このとき、ブランチは「リモートブランチ」としてコピーされてきます。リモートリポジトリからコピーされてきたブランチなので、「リモートブランチ」です。

今は、手元に master ブランチと、clone 元から複製されてきた三つの「リモートブランチ」が存在している状態です。

これらのリモートブランチは、もともと「自分の物」ではありません。「みんなのもの」です。なので、このリモートブランチを選択して作業をすることはできません。では、リモートリポジトリに内容を反映させたいような変更を手元で行うためには、どうすればいいのでしょうか？

手順は以下の通りです。

1. リモートリポジトリの、反映したいブランチを「追跡」するためのブランチを手元のリポジトリに作成する
1. そのブランチ上で変更を行い、コミットする
1. このコミットを、「追跡」しているリモートブランチとリモートリポジトリに反映する

「origin/development」を追跡する development ブランチを、手元に作成しましょう。リモートブランチを追跡するブランチを作成するためには、 

    $ git branch ＜手元のブランチの名前＞ ＜追跡したいリモートブランチの名前＞

です。やってみましょう。

    $ git branch development origin/development
    Branch development set up to track remote branch development from origin.
「development ブランチは、 origin から来た development リモートブランチを追跡するように設定されたよ」と言われましたね。いい感じです。

これで手元の development ブランチで行った反映を origin の development ブランチに反映したり、その逆に origin の development ブランチで行われた変更を自分の development ブランチに適用することができるようになりました。

ところで、さきほど git clone してきたときに、すでに手元に master ブランチが存在していましたね？ これはどういうことでしょうか。

git clone を行ったとき、まずはクローン元のリポジトリに存在するコミットとブランチが手元に複製されるのは上で見た通りです。じつは、Git さんはそのあと、origin/master ブランチを追跡する master ブランチを勝手に手元に作成してくれて、さらに作業ディレクトリ内にこの master ブランチを checkout するところまで自動でやってくれていたのです。


### リモートリポジトリの手動追加
remoteリポジトリを追加するためには、

    $ git remote add <リモートリポジトリの名前> <リモートリポジトリの場所>

です。

アレッ！？ origin/* ブランチがないですね！？

今は「リモートリポジトリはここにあるよ」という設定はしましたが、そのリモートリポジトリに存在しているコミットやブランチを手元のリポジトリにコピーしてくるところまではやっていません。

では、リモートリポジトリに存在するコミットやブランチを手元に持ってきましょう。そのために使うコマンドが、 git fetch です。

    $ git fetch ＜リモートリポジトリの名前＞

で、リモートリポジトリの中身を手元に持って来れます。やってみましょう。

    $ git fetch origin
    From path/to/shared_repo
     * [new branch]      development -> origin/development
     * [new branch]      master     -> origin/master

ふたつの新しいブランチが生まれていますね。矢印の左側が「リモートリポジトリでのブランチの名前」、矢印の右側が「手元にコピーされたリモートブランチ」です。

さて、これで準備は OK でしょうか？

じつは、まだ準備は万端ではありません。手元には development ブランチと master ブランチが存在していますが、このブランチがそれぞれ origin/development と origin/master を追跡するようにしないと、手元で行った変更が origin/development や origin/master に反映されませんね。なので、次は手元の master, development がそれぞれ origin/master, origin/development を追跡するように設定しましょう。

そのためには、

    $ git branch --set-upstream-to=＜追跡したいリモートブランチ＞ ＜手元のブランチ＞

というコマンドを利用します。


### みんなでさわるリポジトリ　まとめ
- 手元のリポジトリでの変更内容を他のリポジトリに反映したり、逆に他のリポジトリでの変更内容を自分のリポジトリに反映するためには、そのリポジトリを「リモートリポジトリ」として登録しておかなくてはいけない
    - git clone でリポジトリを複製した場合、Git が勝手にこの複製もとを「origin」という名前でリモートリポジトリに登録してくれる
    - そうでない場合は、 git remote add <名前> <場所> でリモートリポジトリを登録できる
- リモートリポジトリに存在するブランチやコミットを手元に複製するためには、 git fetch ＜リモートブランチの名前＞ を使う
    - git clone でリポジトリを複製した場合は、clone の段階ですでに手元のリポジトリに複製されている。
    - リモートリポジトリに存在するブランチは、手元のブランチにコピーしてくるときには「リモートブランチ」という形でコピーされる。
- リモートブランチに直接コミットすることはできないので、このリモートブランチを追跡するためのブランチを手元のリポジトリに作成する必要がある。
    - あるリモートブランチを追跡する新しいブランチを作成したい場合は、git branch <新しいブランチ名> <リモートブランチ名>
    - すでに手元に存在するブランチであるリモートブランチを追跡したい場合は git branch --set-upstream-to=＜追跡したいリモートブランチ＞ ＜手元のブランチ＞


### みんなでつかう　push pull
    $ git checkout -b feature/unify_styles development

今回は「feature/unify_styles」という名前のブランチを切っていますね。これは、「このブランチはフィーチャーブランチだよ」ということをわかりやすくするために、こういう名前を付けただけです。しかし、そのあとに development という指定をさらにしてあります。

これはどういうことかと言うと、新しいブランチを「どこから」切るのかを指定したのです。

おそらく、いまゆうすけであるあなたは master ブランチを選択していたでしょう。この状態でgit branch -b ＜新しく作るブランチの名前＞とすると、master ブランチから分岐するブランチが切られます。しかし、

    $ git branch -b ＜新しく作るブランチの名前＞ ＜分岐元＞

とすることで、明示的に「どこからブランチを分岐させるのか」を指定することができるのです。


### リモートリポジトリが存在しない -> push
さて、手元のリポジトリの変更をリモートリポジトリに反映させるためにはどうするのでしたっけ？ そうです、追跡ブランチですね。今回ならば、origin/hotfix を追跡するブランチを作れば…………、とここまで考えて、「アレっ」となりました。そもそも origin/hotfix というリモートブランチが存在しない……。

    $ git push ＜リモートリポジトリの名前＞ ＜手元のブランチ＞:＜リモートに作りたいブランチ＞

これで「リモートリポジトリに新しいブランチを複製」できる

    $ git push origin hotfix:hotfix
    Counting objects: 5, done.
    Delta compression using up to 8 threads.
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (3/3), 371 bytes, done.
    Total 3 (delta 1), reused 0 (delta 0)
    To ../shared_repo.git
     * [new branch]      hotfix -> hotfix
 
 重要なのは最後の 2 行です。「shred_repo.git に対して: ・新しいブランチ hotfix -> hotfix」という感じですね。うん。みんなで触るリポジトリにhotfixを作成することができました。
 
 ちなみに、今回のように、手元のリポジトリでのブランチの名前とリモートリポジトリのブランチの名前が同一の場合は、

    $ git push <リモートリポジトリの名前＞ ＜ブランチの名前＞

でも OK です。


さて、これで「みんなで触るリポジトリ」にhotfixブランチを作成することができました。じゃあ、手元の hotfix ブランチがこのリモートブランチを追跡するように設定しておきましょう。

    $ git branch --set-upstream-to=origin/hotfix hotfix

はい、いいですね。


### 共有リポジトリにマージする

共有リポジトリを直接いじることはできません。そういうときにはどうするのでしたか？ そうです、「追跡ブランチ」を変更すればいいのでしたね。今、共有リポジトリの master ブランチを追跡しているのは、手元の master ブランチです。

では、hotfix の内容を手元の master ブランチに merge しましょう。これは簡単ですね。

    $ git checkout master
    $ git merge --no-ff hotfix 

です。では現在のグラフを確認しましょう。

    $ git log --graph --date-order --all --pretty=format:'%h %d %ad %cn %s' --date=short
    *   0672d53  (HEAD -> master) 2017-01-05 TAKASHI Merge branch 'hotfix'
    |\
    | * 315f673  (origin/hotfix, hotfix) 2017-01-05 TAKASHI 頭おかしいという表現はまずいので修正
    |/
    * 7730680  (origin/master, origin/development, development) 2017-01-05 TAKASHI add cat_lover_said.txt

手元の master ブランチは、できたてのマージコミットを指しています。しかし、origin/master はまだこのマージコミットを指していませんね。それもそのはず、そもそもまだこのコミットは変更者の手元のリポジトリにしか存在しません。

ここで git status を確認すると

    $ git status
    On branch master
    Your branch is ahead of 'origin/master' by 2 commits.
      (use "git push" to publish your local commits)
    nothing to commit, working directory clean

お、初めて見る表示が出てきました。なになに？

「君のブランチは origin/master よりも 2 コミット進んでいるぜ！(もし君の手元のコミットを公開してしまいたければ、 git push するといいぜ！)」だそうです。

では、Gitさんに言われたとおり、ここで git push で共有リポジトリにこの変更を公開しましょう！


    $ git push
    warning: push.default is unset; its implicit value has changed in
    Git 2.0 from 'matching' to 'simple'. To squelch this message
    and maintain the traditional behavior, use:

      git config --global push.default matching

    To squelch this message and adopt the new behavior now, use:

      git config --global push.default simple

    When push.default is set to 'matching', git will push local branches
    to the remote branches that already exist with the same name.

    Since Git 2.0, Git defaults to the more conservative 'simple'
    behavior, which only pushes the current branch to the corresponding
    remote branch that 'git pull' uses to update the current branch.

    See 'git help config' and search for 'push.default' for further information.
    (the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
    'current' instead of 'simple' if you sometimes use older versions of Git)

    Counting objects: 1, done.
    Writing objects: 100% (1/1), 227 bytes | 0 bytes/s, done.
    Total 1 (delta 0), reused 0 (delta 0)
    To ../shared_repo.git
       7730680..0672d53  master -> master

では、warning の内容を読んでみましょう。

    警告： push.default が設定されてないよ。push.defaultが設定されていないとき
    の値は、Git 2.0 で「matching から simple」に変更されるよ。
    以下のようなコマンドを打つと、今後このメッセージは出なくなるし、
    変更されてからも今までと同じ動きをするよ

      git config --global push.default matching

    以下のようなコマンドを打つと、今後このメッセージは出なくなるし
    2.0以降の新しい動きをするようになるよ。

      git config --global push.default simple

    もっと詳しい説明が聞きたければ、'git help config' と打って、
    'push .default'の部分を探してくれよな。
    (ちなみに'simple'モードは Git 1.7.11 から使えるんだ。もし古い Git の
    ヴァージョンを使うようなら、似たような 'current' ってモードを使ってくれ)

だそうです


この push.default というのは、git push 何も後ろに付けずに push を実行したときに、Git さんがどのような動きをするのかを設定する設定項目です。'matching' モードだと、今選択されているブランチがどのブランチかには関係なく、「手元にあるすべての追跡ブランチの変更をリモートに反映する」という動きになります。'simple'モードは、「今選択されているブランチが追跡ブランチであれば、手元のブランチの変更内容をリモートに反映する」という動きになります。

今回は上記設定は、おこなわず、下記にてpushした。

    $ git push [リモートリポジトリ] [ローカルのブランチ名]:[リモートのブランチ名]
    $ git push origin master:master


### あと始末
無事にリリースされたそうです。では、あと始末をしましょう。今からやらなければならないのは大まかに以下の二つです。

- hotfix ブランチはもう用無しなので、手元からもリモートからも消してしまう
- 緊急リリースによる変更内容を、開発ブランチにも反映させる

さあ、ではやっていきましょう。手元の hotfix ブランチを消すのは簡単ですね

    $ git branch -d hotfix

消したっていう内容を反映するために追跡ブランチが必要なんだけど消したっていう内容を生むためには消す必要があって push できない……。という感じですね。そんなわけなんで、リモートのブランチを消すためにはそのためのコマンドを別に打つ必要があります。

    $ git push origin :hotfix

では、次は、 hotfix で対応された内容が反映されている master を、 development に取り込みましょう。

    $ git checkout development
    $ git merge --no-ff master

これをリモートに反映

    $ git push


### 別の開発者：merge
さて、いちいちこうやってリモートリポジトリの内容を取得してきて、手動で merge するのは正直だるいですね。だるすぎです。そのために用意されているの git pull です。

git pull は、「fetch してマージ」という一連の動作を自動でやってくれます。普段はこちらを使うと良いでしょう。ただし、気をつけてください。さきほど "git pull は「fetch してマージ」をという一連の動作を自動でやってくれる" といいました。そうです、「マージ」を行うのです。そのため、git pull を行うと「コンフリクト」が起こる可能性もあります。でも、もうあなたはコンフリクトがおこったおきにどうすればいいか、知っていますね。なら怖がらなくても大丈夫。落ち着いて競合を直し手動でマージコミットを作ればいいのです。

当然、このマージコミットは「手元」にしかないマージコミットなので、適切に共有リポジトリに push する必要も出てくるでしょう。でも、もうあなたはリモートリポジトリと手元のリポジトリの関係を適切にハンドルすることができるようになっています。これもなにも怖くないですね。


### git push 落ち穂ひろい

さて、今回は何事もなくスムースにことが運びましたが、git push が成功するためには、条件があります。

- リモートリポジトリが、bare リポジトリである
    - 覚えてますか？ bare リポジトリ。作業ディレクトリを伴わないリポジトリでしたね。自分が作業してるところにどっかから push されてきたら混乱しちゃいますよね。そのため、作業ディレクトリを持たない bare リポジトリへじゃないと、push は受け入れてもらえません。
- リモートリポジトリへの書き込み権限を持っている
    - 今回は同じファイルシステム上の書き込み権のあるリポジトリだったから push 可能だったけれど、たとえば Github の他人のリポジトリだとか、そういう「書き込み権」のないリポジトリに対して push しても書き込みはできません。まあ、当然ですね。
- 手元のリモートブランチがリモートリポジトリに「追いついて」いる
    - 自分の手元にあるコミットよりもリモートのコミットのほうが「先に」進んでいたら、そのコミットは「あれ。親コミットが違う……」これどうすればいいんだろう……となってしまいます。このような場合には、適宜 git fetch からの merge や git pull を行って(その際の merge ではコンフリクトが発生する可能性があります)、手元のリモートブランチをリモートリポジトリに追いつかせてから push してください。
- すでにリモートリポジトリに push 済みのコミットが、手元のリポジトリで改変されていない
    - push 済みのコミットが git rebase や git commit --amend で改変されてしまうと、リモートリポジトリと手元のリポジトリの間で不整合が起こってしまいます。

### push, pull まとめ
- リモートリポジトリに手元の変更を反映したいなら、git push
    - 追跡ブランチに対しての変更はそのまま git push
    - 新しいブランチを作りたいなら git push ＜リモートリポジトリの名前＞ ＜手元のブランチ＞:＜リモートのブランチの名前＞
    - ブランチを削除したいなら git push ＜リモートリポジトリの名前＞ :＜リモートのブランチの名前＞
- リモートリポジトリから手元に変更を持ってきたいなら git fetch
    - リモートリポジトリのコミットとブランチを持ってくる
    - リモートリポジトリのブランチはリモートブランチとして作られる
- fetch のついでに merge も一緒にやりたいなら、git pull

今後参考になる運用方法　　
1. http://keijinsonyaban.blogspot.jp/2010/10/a-successful-git-branching-model.html　　
2. https://gist.github.com/Gab-km/3705015　　
