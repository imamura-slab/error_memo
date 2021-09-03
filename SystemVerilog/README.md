# SystemVerilog


- Warningはちゃんと読もう!!


***
### コンパイル

<details>
<summary>instance '***' of design unit '***' is unresolved in '*.sv' </summary>

- コンパイル時(Makefile)に依存関係のあるsvファイルを忘れずに含めよう
</details>

<details>
<summary>何をしても同じエラーが出る</summary>

- いじってるファイル間違ってない? 階層をよく見ろ!
</details>



<details>
<summary>if文の記述は合ってるはずなのにエラーが出る</summary>

- A is not constant エラー
- if文を書いている always_ffブロックに入る直前の変数宣言で, 行末を `;` ではなく `,` にしてしまっていた. 
</details>






***
### 動的再構成（Intel FPGA）
<details>
<summary>各revisionのコンパイルでエラーが出る</summary>

- pr_ip作ったあと, ちゃんとインスタンス化した? （コード追加した?）
</details>


<details>
<summary>.rbfファイルがない</summary>

*.qsfに以下の2行を追加する
```
set_global_assignment -name GENERATE_PR_RBF_FILE ON
set_global_assignment -name ON_CHIP_BITSTREAM_DECOMPRESSION OFF
```
</details>






***
### simulation
<details>
<summary>$fdisplay()で記録したログに, ハイインピーダンス(Z)が含まれてしまう</summary>

- 出力信号のbit幅と, それを受け取る(simファイルでの)信号線のbit幅が異なっていた
</details>


<details>
<summary>xやzとの比較をしたい</summary>

- aaa === 'x
  - イコールは3つ
  - シングルクォーテーションは左側だけ
</details>


<details>
<summary>generate文で作ったインスタンスを指定したい</summary>

- `ラベル名[番号].インスタンス名`
```SystemVerilog
	genvar i;
	generate
		for(i=0;i<10;i++)begin : gen
			aaa #(.bbb(bbb)) aaa_inst(.ccc(ccc));
		end
	endgenerate
```
- 0番目のインスタンスを指定したい場合
  - `gen[0].aaa_inst`
</details>


<details>
<summary>simulationが全く進まない</summary>

- clk <= ~clk; のところに #(CLOCK_PERIOD/2) を書いていなかった... 
</details>







***
### 実機
<details>
<summary>LEDが点滅しない</summary>

- resetの極性を良く見なさい
</details>


<details>
<summary>LEDの点滅が速すぎる</summary>

- 1秒のcount間違ってない?
  - 50MHz => 50 * 10**6 = 50000000
</details>




***
### 未解決
- string型の変数をパラメータとしてインスタンスへ渡すとき。
  - たしか Illegal operand for constant expression のエラー
- また、generate文内で上のことをやったとき。







***
<details>
<summary>test</summary>

- test
</details>



