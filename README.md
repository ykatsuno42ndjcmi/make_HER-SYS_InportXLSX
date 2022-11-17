# HER-SYS向けCovid-19発生届一括登録用XLSXファイル作成ツール
　本ツールは、JupyterLabを利用してCovid-19発生届をHER-SYSが配布するテンプレートXLSXファイルをベースに複数対象者を一括登録可能な形式で出力するためのものです。使用するXLSXテンプレートファイルは、HER-SYSより各自ダウンロードしてください。ツールに対応するXLSXは2022/10/28に改訂・配布されたXLSXファイルです。  
　ダウンロード、改修の上使用する場合は、出力・HER-SYS登録を行うデータ内容に関しては保証できませんので、予めご了承ください。
## 動作環境構築
- Windows10Pro 21H2  
- JupyterLab Desktop
  
  [こちら](https://github.com/jupyterlab/jupyterlab-desktop/releases/latest/download/JupyterLab-Setup-Windows.exe)よりexeファイルをダウンロードの上、ウィザードに従ってインストールを行ってください。  
  更新の場合は、[アンインストール](https://github.com/jupyterlab/jupyterlab-desktop/blob/master/user-guide.md#windows)した後、新しいexeから再インストールが必要なのでご注意ください。
- 必要モジュールのインストール
　Install_needs_modules.ipynbを実行して、必要な以下のモジュール一式をインストールします。  
  - jupyterlab-language-pack-ja-JP 3.5.post1
  - Jusho 0.1.0
  - openpyxl 3.0.10
  - chardet 5.0.0
 
## Config.iniファイル設定変更
　以下の項目に対し、フォルダフルパスを設定の上、上書き保存してください。   
　各項目の詳細については、iniファイルを参照してください。  
　TEMPLATEFILE_FULLPATHには、HER-SYSよりダウンロードしたXLSXテンプレートファイルを指定します。  
　※ディレクトリは末尾に”\”を含めて設定してください。
 - [SETTINGS]WORK_DIR
 - [LOG]FOLDERPATH
 - [CSV]READ_FOLDERPATH
 - [CSV]MOVE_FINISHCSV_FOLDERPATH
 - [XLSX]TEMPLATEFILE_FULLPATH
 - [XLSX]SAVE_XLSX_FOLDERPATH
 ## Make_HER-SYS_InportXLSX_V1_0_6.ipynb１セル目の参照先ディレクトリパス変更
 　１セル目２行目のos.chdir内に記載されている'で囲まれているパスをipynbファイルが保存されているディレクトリパスに書き換えます。
 ## Make_HER-SYS_InportXLSX_V1_0_6.ipynb３セル目577行目の郵便番号データベース参照先設定変更
 　[こちら](https://github.com/nagataaaas/Jusho/archive/refs/heads/main.zip)より、Jushoモジュールをダウンロード・解答の後、Jusho-main>jushoフォルダ内にあるdataディレクトリを任意の場所にコピーします。この中にあるaddress.dbが住所-郵便番号変換時に使用されるデータベースとなります。  
　コピーしたディレクトリパスを３セル目577行目の''内に貼り付けます。（※ここでは末尾の\は不要です）
 ## ツール（Make_HER-SYS_InportXLSX_V1_0_6）実行
 　JupyterLab DesktopからMake_HER-SYS_InportXLSX_V1_0_6.ipynbを開きます。  
 　３つのセルですべての処理が実施できます。最初のセルにカーソルをあわせた後、[Shift]+[Enter]キーを３回押下して処理が成功すれば、生成されたXLSXファイルが自動で展開されます。
 ## テストデータ（org_test.csv）について
 　ipynbのDICT_PUBLICHEALTHCARECENTER_CITYに新しい管轄保健所定義を加えれば、患者住所に則して変換が行われます。  
 　デフォルトテストデータでの動きを確認後は、定義情報の追加やテストデータ自体の変更等で動作がどうのように変わるのか、ぜひご確認ください。  
 ## 謝辞
 　郵便番号ラッパーである「[Jusho](https://github.com/nagataaaas/Jusho)」開発者である[Yamato Nagata氏](https://twitter.com/514YJ)に改めまして感謝申し上げます。  
 　またこれまでHER-SYS運営、問い合わせ対応等に携わってこられた厚生労働省新型コロナウイルス感染症対策推進本部戦略班、HER-SYSヘルプデスクはじめとする関係各位の多岐長期間に渡るサポートにも改めて御礼申し上げます。
 ## 結語
 　本ツール公開にあたり、リファクタリング不完全でコードとして読みにくい部分が多々あるかと思います。pythonでのツール開発は本作が処女作であることもあり、個人的にも研鑽を積んでいきたいと考えております。  
 　それでも今回第４２回医療情報学連合大会ポスター発表の機会をいただくにあたり、Covid-19第８波以降に向けて、というよりも（機会としては到来しないことを切に願いますが）新たな新興感染症感染拡大期対応の機会を念頭に、感染症医療機関としての対応一例として関係各位の皆様方への”気づき”やより高度なツールへの”踏み台”としてご活用いただければ幸いです。  
