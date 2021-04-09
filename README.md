# 旗振り検知
## 研究について
- 実装上の難しさ
    - 屋外での作業のため、天候・照明に頑健な認識
    - 作業員ごとの癖によらない認識
    - 旗振り役の（相対的な）位置の変化と旗の変位の検出
- 既存手法
    - 動画認識の既存手法は、optical flow ベースがメイン
        - 例
            - Two-Stream Convolutional Networks [Simonyan et al.,2014]
            - Representation Flow for Action Recognition [AJ Piergiovanni et al.,2019]
        - optical flow ベースの欠点
            - 画像全体に注目し輝度変化を計算するため時間がかかる
            - 速度の検出に関する論文がない（骨格の変化等に注目していないため）
    - 骨格抽出 を利用した手法
        - 例
            - Spatiotemporal Convolution Neural Network [Ma et al., 2018]
            - 自動運転のための手信号の認識システム [Ono et al., 2020]

## 追試する論文の list
- [Two-Stream Convolutional Networks [Simonyan et al.,2014]](https://papers.nips.cc/paper/2014/file/00ec53c4682d36f5c4359f4ae7bd7ba1-Paper.pdf)
- [自動運転のための手信号の認識システム [Ono et al., 2020]](https://https://www.jstage.jst.go.jp/article/seisankenkyu/72/2/72_195/_pdf)
