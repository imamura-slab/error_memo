# System Verilog


<details>
<summary>$fdisplay()で記録したログに, ハイインピーダンス(Z)が含まれてしまう</summary>

- 出力信号のbit幅と, それを受け取る(simファイルでの)信号線のbit幅が異なっていた.
</details>



<details>
<summary>LEDが点滅しない</summary>

- resetの極性を良く見なさい
</details>


<details>
<summary>LEDの点滅が速すぎる</summary>

- 1秒のcount間違ってない?
  - 50MHz => 50 * 10**6 = 50000000
</details>


<details>
<summary>xやzとの比較をしたい</summary>

- aaa === 'x
  - イコールは3つ
  - シングルクォーテーションは左側だけ
</details>


<details>
<summary>instance '***' of design unit '***' is unresolved in '*.sv' </summary>

- Makefileにちゃんと依存関係のあるsvファイルを含める
</details>


<details>
<summary>generate文で作ったインスタンスを指定したい</summary>

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
<summary>test</summary>

- test
</details>



