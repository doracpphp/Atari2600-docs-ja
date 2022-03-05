# 命令セット
- [命令セット](#命令セット)
  - [表綺麗](#表綺麗)
  - [ADC](#adc)
    - [フラグ](#フラグ)
  - [AND](#and)
    - [フラグ](#フラグ-1)
MOS6502なのでMOS6502を参照してください

## 表綺麗
|名称|表記例|動作|
|:----|:----|:----|
|Implied|TAX|AをXにコピー|
|Accumulator|LSR A|Aを左に1bitシフト|
|Immediate|LDA #d8|即値IM8をAにロード|
|Zero page|LDA a8|アドレス「a8」の8bit値をAにロード|
|Zero page, X|LDA a8, X|アドレス「a8 + X」の8bit値をAにロード|
|Zero page, Y|LDA a8, Y|アドレス「a8 + Y」の8bit値をAにロード|
|Relative|BEQ IM8|ステータスレジスタZがオンの時、アドレス「PC + a8」へジャンプ|
|Absolute|LDA a16|アドレス「a16」の8bit値をAにロード|
|Absolute, X|LDA a16, X|アドレス「a16 + X」の8bit値をAにロード|
|Absolute, Y|LDA a16, Y|アドレス「a16 + Y」の8bit値をAにロード|
|(Indirect)|JMP (a16)|アドレス「アドレス「a16」の16bit値」へジャンプ|
|(Indirect, X)|LDA (a8, X)|アドレス「アドレス「a8 + X」の16bit値」の8bit値をAにロード|
|(Indirect), Y|LDA (a8), Y|アドレス「アドレス「a8」の16bit値 + Y」の8bit値をAにロード|


## ADC

```
A + Memory + C -> A, C
```

|モード|アセンブリ|オペコード(Hex)|命令長|サイクル|
|----|------|---|---|---|
|Immediate|     ADC #d8|      $69|  2|   2|
|Zero Page|     ADC a8|       $65|  2|   3|
|Zero Page,X|   ADC a8,X|     $75|  2|   4|
|Absolute|      ADC a16|     $6D|  3|   4|
|Absolute,X|    ADC a16,X|   $7D|  3|   4+|
|Absolute,Y|    ADC a16,Y|   $79|  3|   4+|
|Indirect,X|    ADC (a8,X)|   $61|  2|   6|
|Indirect,Y|    ADC (a8),Y|   $71|  2|   5+|

### フラグ
|N|Z|C|I|D|V|
|:----|:----|:----|:----|:----|:----|
|+|+|+|-|-|+|

## AND
```
A AND Memory -> A
```

|モード|アセンブリ|オペコード(Hex)|命令長|サイクル|
|:----|:----|:----|:----|:----|
|immediate|AND #d8|29|2|2|
|zeropage|AND a8|25|2|3|
|zeropage,X|AND a8,X|35|2|4|
|absolute|AND a8|2D|3|4|
|absolute,X|AND a8,X|3D|3|4*|
|absolute,Y|AND a8,Y|39|3|4*|
|(indirect,X)|AND (a8,X)|21|2|6|
|(indirect),Y|AND (a8),Y|31|2|5*|

### フラグ
|N|Z|C|I|D|V|
|:----|:----|:----|:----|:----|:----|
|+|+|-|-|-|-|
