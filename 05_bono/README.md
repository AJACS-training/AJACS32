## コマンドラインで遺伝子配列を解析する
<hr class="full_hr" />
<p>目次</p>
<div class="contents">
<a id="contents_1"></a>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li><a href="#r2e170d6">  はじめに: 参加者アンケート </a></li>
<li><a href="#xf9175d0">  必要なコンピュータリテラシー </a>
<ul class="list2" style="padding-left:16px;margin-left:16px"><li><a href="#e3077b51">  Google </a></li>
<li><a href="#y1eedffd">  脱線: GGRNA </a></li>
<li><a href="#vef33a7b">  cygwin(windowsの人のみ) </a></li>
<li><a href="#de3fd902">  UNIX コマンド </a></li></ul></li>
<li><a href="#e17b6eed">  Local BLAST </a>
<ul class="list2" style="padding-left:16px;margin-left:16px"><li><a href="#n783a910">  Windows </a></li>
<li><a href="#o5cee03c">  MacOSX </a></li></ul></li>
<li><a href="#z7c0084b">  データ後処理 </a>
<ul class="list2" style="padding-left:16px;margin-left:16px"><li><a href="#y173062b">  数える </a></li>
<li><a href="#dcf9cf96">  ベストヒットだけを抽出 </a></li>
<li><a href="#y8b3afb0">  おまけ：改行コード問題 </a>
<ul class="list3" style="padding-left:16px;margin-left:16px"><li><a href="#yf6119ab">  改行コード問題とは？ </a></li>
<li><a href="#q75d09de">  その対処法 </a></li></ul></li></ul></li></ul>
</div>

<hr class="full_hr" />
<p>事前調査: Mac: 4, Windows: 16, N/A: 1</p>
<h3 id="content_1_0"><a id="r2e170d6" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#r2e170d6" title="r2e170d6"><span class="sanchor">_</span></a> はじめに: 参加者アンケート  </h3>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>おもにMacの人：5</li>
<li>おもにWindowsの人：9</li>
<li>iPhoneの人：4
<ul class="list2" style="padding-left:16px;margin-left:16px"><li>そのうちiPhoneは体の一部の人：2</li></ul></li>
<li>iPadの人:4</li>
<li>バイオインフォマティクスを使っている人：0</li>
<li>プログラミングをたしなむ人：0</li>
<li>データベースを構築している人：0</li>
<li>データベースを構築したい人：0</li>
<li>ライフサイエンス統合データベースセンターの存在を知っていた人：3</li></ul>

<h3 id="content_1_1"><a id="xf9175d0" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#xf9175d0" title="xf9175d0"><span class="sanchor">_</span></a> 必要なコンピュータリテラシー  </h3>

<h3 id="content_1_2"><a id="e3077b51" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#e3077b51" title="e3077b51">_</a> Google  </h3>
<blockquote><p class="quotation"><a href="http://www.google.co.jp/" rel="nofollow">http://www.google.co.jp/</a></p></blockquote>
<p>Google（「グーグル」と読みます）検索することを「ググる」といいます。そこでインターネット上では、自分でインターネット検索もせずにあれこれと質問をしてくるユーザーに対して以下のようにいうことがあります。</p>
<p><span style="font-size:30px;display:inline-block;line-height:130%;text-indent:0px">ググれカス</span></p>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>【実習B1】<strong>DBCLS</strong>でググりなさい。何件ヒットがありますか？



<div class="plugin_fold_body"><p>2012年7月26日現在、約 1,040,000  件</p>
</div></li></ul>
<p>でもこれは「ウェブ全体から検索」した結果なのです。</p>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>【実習B2】ググった結果のページ中で「日本語のページを検索」のリンクを探してクリックしなさい。
<a name="plugin_fold_anchor2"></a>
<div class="plugin_fold_title_plus" onclick="return plugin_fold_onclick(this,event,'plugin_fold_anchor2')"><p>←こたえ。上記の結果と比較してどう変化するでしょうか？</p>
</div>
<div class="plugin_fold_body"><p>2012年7月26日現在、約  593,000 件</p>
</div></li></ul>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>【実習B3】さらに画面最下部の「検索オプション」をクリックして絞り込みをかけてみなさい。<strong>ドメイン</strong>で<em>.ac.jp</em>を指定すると何件ぐらいに絞り込まれますか？
<a name="plugin_fold_anchor3"></a>
<div class="plugin_fold_title_plus" onclick="return plugin_fold_onclick(this,event,'plugin_fold_anchor3')"><p>←こたえ。得られる結果にはどういった特徴があるだろうか？</p>
</div>
<div class="plugin_fold_body"><p>2012年7月26日現在、約15,700 件で、ドメインがdbcls.rois.ac.jpのサイトばかりがヒットしてくるといった特徴がある</p>
</div></li></ul>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>【応用B4】さらに見るべきヒットを絞り込むにはどういうオプションを指定すればいいだろうか？
<a name="plugin_fold_anchor4"></a>
<div class="plugin_fold_title_plus" onclick="return plugin_fold_onclick(this,event,'plugin_fold_anchor4')"><p>←こたえ。</p>
</div>
<div class="plugin_fold_body"><p>例えば、「キーワードを含めない」オプションで<em>rois</em>を指定してみる</p>
</div></li></ul>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>【応用B5】'DBCLS' は「ライフサイエンス統合データベースセンター」の略号であるが、たまに「ライフサイエンス総合データベースセンター」と間違えられる。そう間違えられている例を&quot;で囲うことでインターネット検索エンジンを用いて抽出しなさい。
<a name="plugin_fold_anchor5"></a>
<div class="plugin_fold_title_plus" onclick="return plugin_fold_onclick(this,event,'plugin_fold_anchor5')"><p>←こたえ。</p>
</div>
<div class="plugin_fold_body"><p>&quot;ライフサイエンス総合データベースセンター”でググって、「キーワードを含めない」オプションで<em>ライフサイエンス統合データーベースセンター</em>を指定してみる</p>
</div></li></ul>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>【実習B6】'SPF'でググリなさい。どういったことが起こるか？
<a name="plugin_fold_anchor6"></a>
<div class="plugin_fold_title_plus" onclick="return plugin_fold_onclick(this,event,'plugin_fold_anchor6')"><p>←こたえ。</p>
</div>
<div class="plugin_fold_body"><p>例えば、'DBCLS'でGoogle検索しても「ライフサイエンス統合データベースセンター」以外の'DBCLS'はインターネット上にそれほどないため困らないのであるが、短い略語の場合は同義語がインターネット上に多数存在して調べたい情報に行き着くまでに非常に苦労することになります。</p>
</div></li></ul>
<p>つまり、こういうことです。</p>
<p><span style="font-size:36px;display:inline-block;line-height:130%;text-indent:0px"><a href="http://motdb.dbcls.jp/?plugin=attach&amp;pcmd=open&amp;file=donotgoogle.jpg&amp;refer=AJACS26%2Fbono" rel="nofollow">ググるなあぶない</a></span></p>

<h3 id="content_1_3"><a id="y1eedffd" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#y1eedffd" title="y1eedffd">_</a> 脱線: GGRNA  </h3>
<blockquote><p class="quotation"><a href="http://ggrna.dbcls.jp/" rel="nofollow">http://ggrna.dbcls.jp/</a></p></blockquote>
<p>遺伝子名や断片配列（塩基配列やアミノ酸配列）で<span class="noexists">RefSeq<a href="http://MotDB.DBCLS.jp/?cmd=edit&amp;page=RefSeq&amp;refer=AJACS32%2Fbono">?</a></span>を検索できるサイト。DBCLS謹製。</p>
<p><a href="http://lifesciencedb.jp/image/small_video_icon.png" rel="nofollow"><img src="http://lifesciencedb.jp/image/small_video_icon.png" alt="http://lifesciencedb.jp/image/small_video_icon.png" /></a>
<a href="http://togotv.dbcls.jp/20120124.html" rel="nofollow">GGRNAで遺伝子をGoogleのように検索する</a></p>

<h3 id="content_1_4"><a id="vef33a7b" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#vef33a7b" title="vef33a7b">_</a> cygwin(windowsの人のみ)  </h3>
<p>cygwinをまだインストールしていない人は以下の動画を参考にインストールしてください。</p>
<p><a href="http://lifesciencedb.jp/image/small_video_icon.png" rel="nofollow"><img src="http://lifesciencedb.jp/image/small_video_icon.png" alt="http://lifesciencedb.jp/image/small_video_icon.png" /></a>
<a href="http://togotv.dbcls.jp/20110520.html" rel="nofollow">WindowsでUNIX! 1. Cygwin インストール編</a></p>

<h3 id="content_1_5"><a id="de3fd902" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#de3fd902" title="de3fd902">_</a> UNIX コマンド  </h3>
<p><a href="http://lifesciencedb.jp/image/small_video_icon.png" rel="nofollow"><img src="http://lifesciencedb.jp/image/small_video_icon.png" alt="http://lifesciencedb.jp/image/small_video_icon.png" /></a>
<a href="http://togotv.dbcls.jp/20110929.html" rel="nofollow">WindowsでUNIX! 2. ファイル操作編</a></p>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>cd</li>
<li>pwd</li>
<li>ls</li>
<li>cp</li>
<li>mv</li>
<li>rm</li></ul>
<p><a href="http://lifesciencedb.jp/image/small_video_icon.png" rel="nofollow"><img src="http://lifesciencedb.jp/image/small_video_icon.png" alt="http://lifesciencedb.jp/image/small_video_icon.png" /></a>
<a href="http://togotv.dbcls.jp/20120710.html" rel="nofollow">WindowsでUNIX! 3. ファイル操作応用編</a></p>

[sample.zip](sample.zip)

<ul class="list1" style="padding-left:16px;margin-left:16px"><li>wc</li>
<li>less</li>
<li>gzip</li>
<li>tar</li>
<li>mkdir</li>
<li>find</li></ul>
<p>ここで紹介した以外に大きなファイルを扱う際に先頭の数行だけを表示する head、末尾の数行だけを表示する tailなどがあります。</p>
<blockquote><p class="quotation">% head sample1.fa</p>
<p class="quotation">% tail sample1.fa</p></blockquote>
<p>細かいオプションなどはググるまでもなく</p>
<blockquote><p class="quotation">% man head</p></blockquote>
<p>などすることでマニュアルが参照できます。</p>

<h3 id="content_1_6"><a id="e17b6eed" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#e17b6eed" title="e17b6eed"><span class="sanchor">_</span></a> Local BLAST  </h3>
<p>できる人は統合TVみてどんどん進めてってください。</p>
<p>ひょっとすると今使っているLANの制限で、以下動画の中で指示のあるFTPサイトにアクセス出来ないかもしれません。
BLASTのダウンロードサイト（臨時）として</p>
<blockquote><p class="quotation"><a href="http://dbcls.rois.ac.jp/~bono/docs/120728AJACS/LocalBLAST/" rel="nofollow">http://dbcls.rois.ac.jp/~bono/docs/120728AJACS/LocalBLAST/</a></p></blockquote>
<p>DBのダウンロードサイト（臨時）として</p>
<blockquote><p class="quotation"><a href="http://dbcls.rois.ac.jp/~bono/docs/120728AJACS/db/" rel="nofollow">http://dbcls.rois.ac.jp/~bono/docs/120728AJACS/db/</a></p></blockquote>
<p>を用意したので、こちらから必要なファイルをダウンロードしてください。</p>
<p>Windowsのcygwin上でのLocal BLASTを試みる人は、BLASTのプログラムのFTPサイト（のミラーサイト）</p>
<blockquote><p class="quotation"><a href="http://dbcls.rois.ac.jp/~bono/docs/120728AJACS/LocalBLAST/" rel="nofollow">http://dbcls.rois.ac.jp/~bono/docs/120728AJACS/LocalBLAST/</a>
から</p>
<p class="quotation">ncbi-blast-2.2.26+-ia32-win32.tar.gz (32ビットのwindowsの方）</p>
<p class="quotation">ncbi-blast-2.2.26+-x64-win64.tar.gz (64ビットのwindowsの方)</p></blockquote>
<p>をダウンロードし、以下の統合TVのMacOSX版の方でやってみてください（中上級者向け）。その際、展開したプログラムファイルは</p>
<blockquote><p class="quotation">cp ~/ncbi-blast-2.2.26+/bin/* /usr/local/bin</p></blockquote>
<p>などとしてコマンドサーチパスが通ったところにコピーしておいて下さい。</p>

<h3 id="content_1_7"><a id="n783a910" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#n783a910" title="n783a910">_</a> Windows  </h3>
<p><a href="http://lifesciencedb.jp/image/small_video_icon.png" rel="nofollow"><img src="http://lifesciencedb.jp/image/small_video_icon.png" alt="http://lifesciencedb.jp/image/small_video_icon.png" /></a>
<a href="http://togotv.dbcls.jp/20110119.html" rel="nofollow">Local BLAST の使い方～導入・準備編～ 2011</a></p>
<p><a href="http://lifesciencedb.jp/image/small_video_icon.png" rel="nofollow"><img src="http://lifesciencedb.jp/image/small_video_icon.png" alt="http://lifesciencedb.jp/image/small_video_icon.png" /></a>
<a href="http://togotv.dbcls.jp/20110225.html" rel="nofollow">Local BLAST の使い方～検索実行・オプション編～ 2011</a></p>
<p>使用するテスト配列のファイルはこちらです。</p>

[test.txt](test.txt)

[test1.txt](test1.txt)

[testnt.txt](testnt.txt)

[testdouble.txt](testdouble.txt)


<h3 id="content_1_8"><a id="o5cee03c" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#o5cee03c" title="o5cee03c">_</a> MacOSX  </h3>
<p><a href="http://lifesciencedb.jp/image/small_video_icon.png" rel="nofollow"><img src="http://lifesciencedb.jp/image/small_video_icon.png" alt="http://lifesciencedb.jp/image/small_video_icon.png" /></a>
<a href="http://togotv.dbcls.jp/20110420.html" rel="nofollow">Local BLAST の使い方～導入・準備編(MacOSX版)～ 2011</a></p>
<p><a href="http://lifesciencedb.jp/image/small_video_icon.png" rel="nofollow"><img src="http://lifesciencedb.jp/image/small_video_icon.png" alt="http://lifesciencedb.jp/image/small_video_icon.png" /></a>
<a href="http://togotv.dbcls.jp/20110608.html" rel="nofollow">Local BLAST の使い方～検索実行・オプション編(MacOSX版)～ 2011</a></p>
<p>使用するテスト配列のファイルはこちらです。</p>

[test.txt](test.txt)

[test1.txt](test1.txt)

[testnt.txt](testnt.txt)

[testdouble.txt](testdouble.txt)


<h3 id="content_1_9"><a id="z7c0084b" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#z7c0084b" title="z7c0084b"><span class="sanchor">_</span></a> データ後処理  </h3>

<h3 id="content_1_10"><a id="y173062b" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#y173062b" title="y173062b">_</a> 数える  </h3>
<p>大規模にBLASTを計算するといくつヒットがあったかなどが一目ではわからなくなってきます。そういった「数える」必要があるときにコマンドラインでの処理が役に立ちます。</p>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>FASTAファイルの配列のエントリ数を。例えば、上で用いたyeastのアミノ酸配列のDB(FASTA形式)の配列エントリ数を数える場合。
<blockquote><p class="quotation">grep -c ^\&gt; yeast.aa</p></blockquote></li></ul>
<p>6298と出れば正解です。これが（データベース中の）yeastのアミノ酸配列数です。</p>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>BLASTの結果ファイル（-outfmt 6オプションでタブ区切り出力したもの）で、ヒットのあったエントリ数を。自分で結果ファイルを用意しても構いませんが、ここでは以下の結果ファイルのサンプル（ファイル名：testfmt6.out）で説明します。</li></ul>
<div class="img_margin" style="text-align:left"><a href="http://MotDB.DBCLS.jp/?plugin=attach&amp;refer=AJACS32%2Fbono&amp;openfile=testfmt6.out" title="2012/07/26 11:51:26 303.6KB"><img src="image/file.png" width="20" height="20" alt="file" style="border-width:0px" />testfmt6.out</a></div>

<p>処理する前にこれがどんなファイルか見ましょう。</p>
<blockquote><p class="quotation">less testfmt6.out</p></blockquote>
<p>一行が長くて見づらいですね。lessのオプションに-S （Sは大文字のS）というものがあります。すると…。</p>
<blockquote><p class="quotation">less -S testfmt6.out</p></blockquote>
<p>見やすくなりましたね。</p>
<ul class="list2" style="padding-left:32px;margin-left:32px"><li>1カラム目（一番左のカラム）を抜き出し(cut -f1)、ソートして重なりのない状態にして(sort -u)出力する。</li></ul>
<blockquote><p class="quotation">cut -f1 testfmt6.out | sort -u | less</p></blockquote>
<p>さらに、数える(wc)。</p>
<blockquote><p class="quotation">cut -f1 testfmt6.out | sort -u | wc</p></blockquote>
<p>これによってヒットがあったクエリの数が数えられます。これぐらいの数なら人の目でも数えられますが、多くなると不可能になってくるので、こういうコマンドが大変重宝します。</p>
<ul class="list2" style="padding-left:32px;margin-left:32px"><li>ヒットのあったDB中のエントリが記載されている2カラム目を抜き出し(cut -f2)、
<ul class="list3" style="padding-left:16px;margin-left:16px"><li>ソートして(sort)数える(wc)。
<blockquote><p class="quotation">cut -f2 testfmt6.out | sort | wc</p></blockquote></li></ul></li></ul>
<ul class="list3" style="padding-left:48px;margin-left:48px"><li>ソートして重なりのない状態にして(sort -u)数える(wc)。
<blockquote><p class="quotation">cut -f2 testfmt6.out | sort -u | wc</p></blockquote></li></ul>
<p>この違いは重複したエントリによるものです。それが何回でてきたか知るには？</p>
<ul class="list2" style="padding-left:32px;margin-left:32px"><li>ヒットのあった数をそれぞれのエントリごとに。count.prlというPerlスクリプトを使って。</li></ul>
<blockquote><p class="quotation">which perl</p></blockquote>
<p>といれて</p>
<blockquote><p class="quotation">$ which perl</p>
<p class="quotation">which: no perl in (/usr/local/bin:/usr/bin:/cygdrive/c/<span class="noexists">ProgramFiles<a href="http://MotDB.DBCLS.jp/?cmd=edit&amp;page=ProgramFiles&amp;refer=AJACS32%2Fbono">?</a></span>/Parallels/<span class="noexists">ParallelsTools<a href="http://MotDB.DBCLS.jp/?cmd=edit&amp;page=ParallelsTools&amp;refer=AJACS32%2Fbono">?</a></span>/Applications:/cygdrive/c/Windows/system32:/cygdrive/c/Windows:/cygdrive/c/Windows/System32/Wbem:/cygdrive/c/Windows/System32/<span class="noexists">WindowsPowerShell<a href="http://MotDB.DBCLS.jp/?cmd=edit&amp;page=WindowsPowerShell&amp;refer=AJACS32%2Fbono">?</a></span>/v1.0:/cygdrive/c/Program Files/<span class="noexists">MacType<a href="http://MotDB.DBCLS.jp/?cmd=edit&amp;page=MacType&amp;refer=AJACS32%2Fbono">?</a></span>)</p></blockquote>
<p>のように no perl と出たらPerlがインストールされていません。cygwinのインストール画面でオプション設定でPerlをインストールしてください。ちなみにMacOSXの場合は買った状態でPerlがインストールされています。</p>
<blockquote><p class="quotation">while(&lt;&gt;) {</p>
<p class="quotation">my($word) = split;</p>
<p class="quotation">$num{$word}++;</p>
<p class="quotation">}</p>
<p class="quotation">foreach (sort keys %num) {</p>
<p class="quotation">print &quot;$_\t$num{$_}\n&quot;;</p>
<p class="quotation">}</p></blockquote>
<blockquote><p class="quotation">cut -f2 testfmt6.out | sort | perl count.prl | less</p></blockquote>

<h3 id="content_1_11"><a id="dcf9cf96" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#dcf9cf96" title="dcf9cf96">_</a> ベストヒットだけを抽出  </h3>
<p>BLASTの出力ファイル（-outfmt 6オプションでタブ区切り出力したもの）をテキスト処理するやり方もありますが、Local BLASTが実行可能となった今、普通にBLASTのオプションで -max_target_seqs 1 を指定するほうが早いです。例えば、</p>
<blockquote><p class="quotation">blastp -db yeast.aa -query mito.aa -out mito_vs_yeast.out -outfmt 6 -max_target_seqs 1</p></blockquote>
<p>これでquery: mito.aa db: yeast.aaのベストヒットが抽出できます。</p>

<h3 id="content_1_12"><a id="y8b3afb0" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#y8b3afb0" title="y8b3afb0">_</a> おまけ：改行コード問題  </h3>
<p>出てきたBLASTの結果。テキストファイルなのにある種のソフトウェアではうまく認識されないことがあります。その場合、この問題を疑ってください。</p>

<h4 id="content_1_13"><a id="yf6119ab" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#yf6119ab" title="yf6119ab">_</a> 改行コード問題とは？  </h4>
<p>使用プラットフォーム(OS)によって改行コードが異なるため、、</p>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>Macのテキストファイル

[mac.txt](mac.txt)

<blockquote><p class="quotation">% od -c mac.txt</p>
<p class="quotation">0000000   c   a   r   r   i   a   g   e       r   e   t   u   r   n  \r</p>
<p class="quotation">0000020   m   a   c</p></blockquote></li></ul>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>Unixのテキストファイル

[unix.txt](unix.txt)

<blockquote><p class="quotation">% od -c unix.txt</p>
<p class="quotation">0000000   l   i   n   e       f   e   e   d  \n   u   n   i   x</p>
<p class="quotation">0000016</p></blockquote></li></ul>
<ul class="list1" style="padding-left:16px;margin-left:16px"><li>Windowsのテキストファイル

[win.txt](win.txt)

<blockquote><p class="quotation">% od -c win.txt</p>
<p class="quotation">0000000   C   R       a   n   d       L   F  \r  \n   w   i   n</p>
<p class="quotation">0000016</p></blockquote></li></ul>

<h4 id="content_1_14"><a id="q75d09de" href="http://MotDB.DBCLS.jp/?AJACS32%2Fbono#q75d09de" title="q75d09de">_</a> その対処法  </h4>
<p>いくつかやり方がありますが、一番汎用性の高いものを紹介します。</p>
<p>以下のperlワンライナーでmac改行形式のファイル(mac.txt)がUNIX改行形式のファイル(mac_conv_unix.txt)に変換されます。</p>
<blockquote><p class="quotation">perl  -pe 's/\r/\n/g' mac.txt &gt; mac_conv_unix.txt</p></blockquote>
<p><span style="font-size:30px;display:inline-block;line-height:130%;text-indent:0px">つぶやけ、されば救われん</span></p>
