# 旗振り検知
## 研究について
- 実装上の難しさ
    - 屋外での作業のため、天候・照明に頑健な認識
    - 作業員ごとの癖によらない認識
    - 旗振り役の（相対的な）位置の変化と旗の変位の検出
- 既存手法（動画認識手法を適応することを考える場合）
    - 動画認識の既存手法は、optical flow ベースがメイン
        - 例
            - Two-Stream Convolutional Networks [Simonyan et al., 2014]
            - Representation Flow for Action Recognition [AJ Piergiovanni et al., 2019]
        - optical flow ベースの欠点
            - 画像全体に注目し輝度変化を計算するため時間がかかる
            - 速度の検出に関する論文がない（骨格の変化等に注目していないため）
    - 骨格抽出 を利用した手法
        - 例
            - Spatiotemporal Convolution Neural Network [Ma et al., 2018]
            - 自動運転のための手信号の認識システム [Ono et al., 2020]
        - 骨格抽出ベースの欠点
            - 旗の色は検出できない
## 追試する論文の list
- [Optical Flow I [Guido Gerig et al., 2012]](http://www.sci.utah.edu/%7Egerig/CS6320-S2013/Materials/CS6320-CV-S2012-OpticalFlow-I.pdf) の実装が提供されているLucas–Kanade法とGunnar Farneback法
- [Two-Stream Convolutional Networks [Simonyan et al., 2014]](https://papers.nips.cc/paper/2014/file/00ec53c4682d36f5c4359f4ae7bd7ba1-Paper.pdf)
- [Representation Flow for Action Recognition [AJ Piergiovanni et al., 2019]](https://openaccess.thecvf.com/content_CVPR_2019/papers/Piergiovanni_Representation_Flow_for_Action_Recognition_CVPR_2019_paper.pdf)
- [自動運転のための手信号の認識システム [Ono et al., 2020]](https://https://www.jstage.jst.go.jp/article/seisankenkyu/72/2/72_195/_pdf)
## 追試結果
- Optical Flow
    - Lucas–Kanade法
        - ![opticalflow_sparse](https://user-images.githubusercontent.com/71982294/115234390-f170ef80-a153-11eb-889f-02e54be14915.jpg)
    - Gunnar Farneback法
        - ![opticalflow_dense](https://user-images.githubusercontent.com/71982294/115234602-3137d700-a154-11eb-9af7-dadba0430502.jpg)
## 追試予定
- Two-Stream Convolutional Networks
    - [code](https://github.com/jeffreyyihuang/two-stream-action-recognition/blob/master/spatial_cnn.py)
        - spatial_cnn.pyの43行目(ucf_list ='/home/ubuntu/cvlab/pytorch/ucf101_two_stream/github/UCF_list/')でエラーが起きている状況
- Representation Flow
    - [code](https://github.com/piergiaj/representation-flow-cvpr19)
        - 出てきたエラーは解決済み。データセットの動画が大量にありダウンロードして研究室のサーバが壊れそうなので一時中断
- 自動運転のための手信号の認識システム
    - コードは見つからない → 自分で実装
        - 結果
            - 精度 50% 程度
        - 考えられる要因
            - fps が小さすぎてフレーム間での動きが大きい
            - fps が小さいが故に N が大きくとれない（現場ではせいぜい2秒程度の動画で判断しなければ事故につながるため） 
## 中間発表まで
- [ ] 転移学習についてのサーベイ（→スライドに具体例など追加）
    - 論文リスト
- [ ] コメントを元にしたスライドの修正
- [ ] 動画
