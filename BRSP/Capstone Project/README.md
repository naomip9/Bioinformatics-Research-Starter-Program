Analisis Transkriptomik untuk Mengidentifikasi Gen dan Jalur Biologis yang Terderegulasi pada Kanker Serviks Menggunakan Dataset GSE9750

Pendahuluan

Dataset GSE9750 telah digunakan dalam studi sebelumnya untuk mengidentifikasi gen-gen yang overexpressed akibat jumlah salinan di kromosom lengan 20q, yang berkontribusi pada progresi kanker serviks. Temuan tersebut memperkuat relevansi dataset ini dalam menggambarkan kekhasan molekuler dari karsinogenesis serviks, dan menjadi acuan pembanding saat menginterpretasi hasil DEG dan enrichment pathway dalam analisis ini.
Tujuan penelitian ini adalah mengidentifikasi gen dan jalur biologis yang mengalami deregulasi secara signifikan antara sel serviks normal dan sel kanker serviks, guna memahami mekanisme molekuler yang mendasari proses karsinogenesis serta menemukan kandidat biomarker potensial.

Metode
Data transcriptomik diperoleh dari National Center for Biotechnology Information (NCBI) Gene Expression Omnibus (GEO) dengan nomor akses GSE9750, yang merupakan dataset microarray jaringan serviks berbasis platform Affymetrix. Sampel dalam dataset dikelompokkan menjadi dua kategori, yaitu Normal Cervical Cell (NCC) dan Cervical Cancer Cell (CCC). Analisis diferensial ekspresi gen awal dilakukan menggunakan fitur GEO2R yang tersedia pada laman GEO. GEO2R memanfaatkan paket limma (Linear Models for Microarray Data) dalam lingkungan R untuk menghitung perbedaan ekspresi antar kelompok melalui pendekatan model linier dan empirical Bayes moderation. Dalam pengaturan analisis, Group 1 ditetapkan sebagai NCC dan Group 2 sebagai CCC, sehingga nilai log fold change (logFC) merepresentasikan perbedaan ekspresi antara jaringan normal dan kanker (NCC − CCC).
Gen yang dianggap terdiferensiasi secara signifikan ditentukan berdasarkan nilai adjusted p-value < 0,05 menggunakan koreksi Benjamini-Hochberg serta nilai |logFC| > 1. Hasil analisis dari GEO2R kemudian diunduh dalam format tabel dan dianalisis lebih lanjut menggunakan RStudio untuk proses penyaringan gen signifikan, visualisasi (volcano plot dan heatmap), serta analisis fungsional melalui Gene Ontology (GO) dan KEGG pathway enrichment. Interpretasi biologis dilakukan dengan mengaitkan gen-gen signifikan dan jalur yang diperkaya dengan literatur ilmiah yang relevan mengenai mekanisme molekuler kanker serviks.

Hasil dan Interpretasi

Pengolahan data menggunakan GEO2R dijelaskan melalui diagram dan plot berikut.
 
Gambar 1. Mean difference plot pada kelompok gen CCC dan NCC

Mean–Difference plot digunakan untuk memvisualisasikan hubungan antara rata-rata tingkat ekspresi gen dan perubahan ekspresi antara kelompok Cervical Cancer Cells (CCC) dan Normal Cervical Cells (NCC). Pada plot ini, sumbu horizontal menunjukkan nilai rata-rata ekspresi gen (log2 expression), sedangkan sumbu vertikal menunjukkan nilai log fold change (logFC) yang merepresentasikan perbedaan ekspresi antara kedua kelompok. Titik-titik pada plot merepresentasikan probe gen dari platform microarray. Sebagian besar gen terlihat terdistribusi di sekitar nilai logFC nol, yang menunjukkan bahwa banyak gen tidak mengalami perubahan ekspresi yang signifikan. Namun demikian, terdapat sejumlah gen yang menyimpang jauh dari garis tengah baik ke arah positif maupun negatif, yang menunjukkan adanya gen dengan peningkatan atau penurunan ekspresi yang signifikan pada sel kanker serviks dibandingkan sel serviks normal.


Gambar 2. Volcano plot dari gen yang mengalami up-regulasi dan down-regulasi

Volcano plot digunakan untuk menggambarkan hubungan antara besar perubahan ekspresi gen dan tingkat signifikansi statistik dari hasil analisis diferensial. Pada plot ini, sumbu horizontal menunjukkan nilai log2 fold change, sedangkan sumbu vertikal menunjukkan –log10 p-value, yang mencerminkan tingkat signifikansi perubahan ekspresi gen. Titik berwarna merah dan biru menunjukkan gen yang memenuhi kriteria signifikan dengan adjusted p-value < 0,05, sedangkan titik berwarna abu-abu menunjukkan gen yang tidak signifikan. Gen yang berada pada bagian atas plot menunjukkan tingkat signifikansi yang tinggi, sedangkan gen yang berada jauh di sisi kanan atau kiri menunjukkan perubahan ekspresi yang besar. Distribusi titik pada plot ini menunjukkan bahwa terdapat sejumlah gen yang mengalami peningkatan maupun penurunan ekspresi secara signifikan pada sel kanker serviks dibandingkan dengan sel normal, yang mengindikasikan adanya perubahan ekspresi gen yang luas yang berkaitan dengan proses karsinogenesis.

  
Gambar 3. UMAP plot 

Visualisasi menggunakan UMAP (Uniform Manifold Approximation and Projection) digunakan untuk mereduksi dimensi data ekspresi gen yang sangat besar menjadi dua dimensi. Hasil plot menunjukkan bahwa sampel CCC dan NCC membentuk dua klaster yang relatif terpisah, menunjukkan bahwa pola ekspresi gen pada sel kanker serviks berbeda secara sistematis dari sel normal. Pemisahan ini memperkuat hasil analisis diferensial gen dan menunjukkan bahwa perubahan ekspresi gen dapat digunakan untuk membedakan kondisi biologis antara jaringan kanker dan jaringan normal.


Gambar 4. Diagram venn
Hasil analisis diferensial menggunakan metode limma dengan kriteria adjusted p-value < 0.05 menunjukkan adanya sejumlah besar gen yang mengalami perubahan ekspresi antara kelompok kanker serviks (CCC) dan sel serviks normal (NCC). Diagram menunjukkan sekitar 11.974 gen yang teridentifikasi sebagai berbeda secara signifikan, sedangkan sekitar 10.291 gen tidak menunjukkan perbedaan signifikan. Jumlah gen yang berbeda secara signifikan ini menunjukkan bahwa transformasi sel normal menjadi sel kanker serviks melibatkan perubahan ekspresi gen yang luas dalam genom.

 
Gambar 5. Boxplot distribusi nilai ekspresi gen

Boxplot distribusi nilai ekspresi gen menunjukkan sebaran nilai ekspresi pada setiap sampel dalam dataset GSE9750 yang terdiri dari kelompok CCC dan NCC. Secara umum, median dan rentang distribusi ekspresi antar sampel terlihat relatif konsisten, yang menunjukkan bahwa data telah melalui proses normalisasi dengan baik dan tidak terdapat outlier yang ekstrem. Keseragaman distribusi ini penting untuk memastikan bahwa perbedaan ekspresi gen yang teridentifikasi pada tahap analisis selanjutnya benar-benar disebabkan oleh perbedaan biologis antara kelompok kanker dan normal, bukan akibat variasi teknis selama proses pengukuran.


Gambar 6. Densitas ekspresi gen

Diagram densitas ekspresi gen memperlihatkan distribusi nilai intensitas ekspresi untuk seluruh sampel pada kedua kelompok. Kurva distribusi antar sampel menunjukkan pola yang relatif serupa, yang menandakan bahwa data telah terstandarisasi dengan baik dan tidak terdapat perbedaan distribusi yang ekstrem antar sampel. Meskipun demikian, terdapat sedikit pergeseran distribusi antara kelompok kanker dan normal yang dapat mencerminkan perubahan global dalam aktivitas transkripsi akibat proses karsinogenesis.

 
Gambar 7. Distribusi nilai adjusted p-value

Histogram distribusi adjusted p-value menunjukkan sebagian besar gen memiliki nilai p-adjusted yang tinggi, yang berarti tidak mengalami perubahan ekspresi yang signifikan. Namun, terdapat sejumlah gen dengan nilai p-adjusted sangat rendah yang mengindikasikan adanya perbedaan ekspresi yang kuat antara kelompok kanker dan normal. Distribusi ini menunjukkan bahwa hanya sebagian kecil gen yang benar-benar berkontribusi terhadap perbedaan biologis yang diamati.


Gambar 8. Plot kuantil moderated t-statistic

Plot kuantil dari moderated t-statistic menunjukkan bagaimana distribusi statistik uji dibandingkan dengan distribusi teoritis. Sebagian besar titik mengikuti pola garis diagonal, menunjukkan bahwa model statistik yang digunakan cukup sesuai dengan distribusi data. Namun, beberapa titik yang menyimpang pada bagian ekor menunjukkan adanya gen dengan nilai statistik yang sangat tinggi atau rendah, yang kemungkinan merupakan kandidat gen dengan perubahan ekspresi paling signifikan antara kelompok kanker dan normal.

Gambar 9. Plot mean-variance trend

Plot mean-variance trend menunjukkan hubungan antara rata-rata ekspresi gen dan variansinya pada seluruh probe microarray. Pola yang terlihat menunjukkan bahwa gen dengan tingkat ekspresi yang lebih tinggi cenderung memiliki variansi yang lebih rendah dibandingkan gen dengan ekspresi rendah. Hubungan ini merupakan karakteristik umum data microarray dan menjadi dasar penerapan metode statistik seperti moderated t-test pada limma, yang mempertimbangkan estimasi variansi yang lebih stabil untuk meningkatkan akurasi deteksi gen yang berbeda secara signifikan.

Secara keseluruhan, analisis transkriptomik pada dataset GSE9750 menunjukkan adanya perbedaan pola ekspresi gen yang jelas antara sel kanker serviks dan sel serviks normal. Visualisasi seperti boxplot dan density plot menunjukkan kualitas data yang baik setelah normalisasi, sementara analisis UMAP dan identifikasi gen diferensial mengindikasikan adanya pemisahan biologis yang jelas antara kedua kelompok sampel. Sejumlah gen yang berbeda secara signifikan kemudian dapat digunakan untuk analisis lanjutan, seperti analisis pathway dan identifikasi kandidat biomarker yang berperan dalam perkembangan kanker serviks.


Tabel 1. Top 10 DEG Signifikan
Gene Name
logFC
AveExpr
t
P.Value
adj.P.Val
B
205225_at
-2477.683929
1271.137879
-13.31748247
3.2767250791815e-20
7.30152649394014e-16
1.097298584
207935_s_at
-23869.12083
12622.0803
-12.53704752
5.57379806837493e-19
6.21004711787993e-15
0.886709642
205363_at
-512.6428571
231.0560606
-11.59286438
1.902645642002e-17
1.16478516667726e-13
0.599816267
221841_s_at
-5626.78869
2919.712121
-11.56802319
2.09089470300635e-17
1.16478516667726e-13
0.591755306
204751_x_at
-1650.941071
862.230303
-11.43528662
3.46587003577221e-17
1.54459964014224e-13
0.548215598
213533_at
-220.1797619
148.0106061
-11.35648422
4.68314786223937e-17
1.73924306357133e-13
0.521991602
218990_s_at
-27353.27857
13613.88485
-11.15013219
1.03356548605455e-16
3.2901342465362e-13
0.451973461
201667_at
-4084.642857
2747.748485
-11.07275365
1.39252493583708e-16
3.87870414315721e-13
0.425207716
211597_s_at
-6764.497024
2782.657576
-10.99398679
1.88752267968065e-16
4.6732964301471e-13
0.39767198
203585_at
-2727.633333
1680.583333
-10.72047641
5.45601884803993e-16
1.21576467990874e-12
0.299750223


Tabel ini menampilkan sepuluh gen dengan perubahan ekspresi paling signifikan antara kelompok CCC dan NCC berdasarkan hasil analisis diferensial menggunakan metode limma. Gen-gen tersebut dipilih berdasarkan nilai adjusted p-value yang paling kecil, yang menunjukkan tingkat signifikansi statistik yang tinggi setelah dilakukan koreksi multiple testing menggunakan metode Benjamini–Hochberg.
Kolom Gene Name menunjukkan ID probe dari platform microarray Affymetrix yang digunakan pada dataset GSE9750. Kolom logFC (log fold change) menunjukkan besarnya perubahan ekspresi gen antara kelompok kanker dan normal dalam skala log2. Nilai logFC negatif menunjukkan bahwa gen tersebut memiliki ekspresi yang lebih rendah pada kelompok kanker dibandingkan kelompok normal, sedangkan nilai positif menunjukkan peningkatan ekspresi pada kelompok kanker.
Kolom AveExpr menunjukkan rata-rata tingkat ekspresi gen di seluruh sampel yang dianalisis. Kolom t merupakan nilai statistik uji moderated t-statistic yang dihasilkan oleh metode limma, yang digunakan untuk menilai signifikansi perbedaan ekspresi gen antar kelompok. Semakin besar nilai absolut t-statistic, semakin kuat bukti bahwa gen tersebut berbeda ekspresinya.
Kolom P.Value menunjukkan nilai p dari uji statistik, sedangkan adj.P.Val merupakan nilai p yang telah dikoreksi untuk mengurangi kemungkinan kesalahan akibat pengujian banyak gen secara bersamaan. Dalam analisis ini, gen dengan nilai adj.P.Val < 0.05 dianggap sebagai gen yang berbeda secara signifikan. Kolom terakhir, B, menunjukkan nilai log-odds bahwa suatu gen benar-benar berbeda secara signifikan antara kedua kondisi.
Berdasarkan tabel tersebut, sepuluh gen teratas menunjukkan nilai adjusted p-value yang sangat kecil, yang mengindikasikan bahwa gen-gen tersebut merupakan kandidat kuat yang terlibat dalam perubahan biologis antara jaringan kanker serviks dan jaringan serviks normal. Gen-gen ini berpotensi menjadi kandidat biomarker atau target penelitian lebih lanjut dalam memahami mekanisme molekuler perkembangan kanker serviks.
Gen-gen dengan perubahan ekspresi paling signifikan kemudian digunakan sebagai dasar untuk analisis lanjutan, seperti analisis enrichment Gene Ontology (GO) dan pathway KEGG untuk mengidentifikasi proses biologis dan jalur molekuler yang terlibat dalam perkembangan kanker serviks.
Analisis menggunakan RStudio dijelaskan melalui volcano plot dan heatmap berikut.


Gambar 10. RStudio volcano plot
Volcano plot digunakan untuk memvisualisasikan hasil analisis differential gene expression antara kelompok CCC dan NCC. Pada plot ini, sumbu horizontal menunjukkan nilai log2 fold change (logFC) yang merepresentasikan besar perubahan ekspresi gen, sedangkan sumbu vertikal menunjukkan –log10 adjusted p-value, yang menggambarkan tingkat signifikansi statistik.
Titik berwarna merah menunjukkan gen yang memenuhi kriteria signifikan (adj.P.Val < 0.05 dan |logFC| > 1), sedangkan titik abu-abu menunjukkan gen yang tidak signifikan. Distribusi titik pada plot menunjukkan bahwa sejumlah besar gen mengalami perubahan ekspresi yang signifikan antara kedua kelompok. Beberapa gen terlihat memiliki nilai logFC yang sangat besar serta nilai p yang sangat kecil, yang menunjukkan adanya perubahan ekspresi yang kuat dan signifikan secara statistik pada sel kanker dibandingkan sel normal. Gen-gen tersebut berpotensi menjadi kandidat biomarker atau gen yang berperan penting dalam proses perkembangan kanker serviks.


Gambar 11. Heatmap
Heatmap digunakan untuk memvisualisasikan pola ekspresi gen yang paling berbeda antara kelompok CCC dan NCC. Pada heatmap ini, setiap baris merepresentasikan gen, sedangkan setiap kolom merepresentasikan sampel. Warna merah menunjukkan tingkat ekspresi gen yang lebih tinggi, sementara warna biru menunjukkan ekspresi gen yang lebih rendah.
Hasil clustering hirarkis menunjukkan adanya pemisahan yang cukup jelas antara kelompok sampel kanker dan normal berdasarkan pola ekspresi gen. Sampel dalam kelompok yang sama cenderung berkumpul dalam klaster yang sama, yang menunjukkan bahwa gen-gen yang dipilih memiliki pola ekspresi yang konsisten dalam membedakan kedua kondisi biologis. Pola ini mengindikasikan bahwa perubahan ekspresi gen memainkan peran penting dalam perbedaan karakteristik molekuler antara sel kanker serviks dan sel serviks normal.


Gambar 12. Diagram analisis gene ontology (GO)
Analisis Gene Ontology (GO) pada kategori Biological Process digunakan untuk mengidentifikasi proses biologis yang paling dipengaruhi oleh gen-gen yang berbeda ekspresinya. Plot menunjukkan beberapa proses biologis yang diperkaya secara signifikan, seperti regulasi proses metabolik DNA, perkembangan sel, pembelahan nukleus, pemisahan kromosom, replikasi DNA, dan signaling checkpoint siklus sel.
Proses-proses tersebut berkaitan erat dengan regulasi siklus sel dan replikasi DNA, yang merupakan mekanisme penting dalam pembelahan sel. Pada sel kanker, proses-proses ini sering mengalami disregulasi sehingga menyebabkan proliferasi sel yang tidak terkendali. Oleh karena itu, hasil analisis GO ini mendukung hipotesis bahwa perubahan ekspresi gen dalam dataset GSE9750 berhubungan dengan mekanisme molekuler yang mengatur pertumbuhan dan pembelahan sel pada kanker serviks.

Gambar 13. Diagram analisis KEGG enrichment pathway
Analisis KEGG pathway enrichment dilakukan untuk mengidentifikasi jalur biologis yang secara signifikan diperkaya oleh gen-gen yang mengalami perubahan ekspresi. Pada plot ini, sumbu horizontal menunjukkan GeneRatio, yaitu proporsi gen yang terlibat dalam suatu pathway dibandingkan dengan total gen yang dianalisis. Ukuran lingkaran menunjukkan jumlah gen yang terlibat dalam pathway tersebut, sedangkan warna lingkaran menunjukkan tingkat signifikansi (adjusted p-value).
Beberapa pathway yang teridentifikasi antara lain PI3K-Akt signaling pathway, Rap1 signaling pathway, proteoglikan dalam kanker, siklus sel, dan penuaan seluler. Jalur-jalur ini diketahui berperan penting dalam regulasi proliferasi sel, diferensiasi, dan kelangsungan hidup sel. Aktivasi atau disregulasi pathway tersebut sering ditemukan pada berbagai jenis kanker, termasuk kanker serviks. Temuan ini menunjukkan bahwa perubahan ekspresi gen dalam dataset GSE9750 berpotensi memengaruhi jalur molekuler yang berhubungan dengan proses karsinogenesis.
Hasil analisis DEG pada dataset GSE9750 menunjukkan sejumlah gen yang mengalami perubahan ekspresi secara signifikan antara sel serviks normal dan sel kanker serviks. Beberapa gen dengan tingkat signifikansi tinggi diidentifikasi sebagai kandidat biomarker potensial yang terkait dengan proses karsinogenesis. Di antaranya adalah gen yang terlibat dalam regulasi siklus sel dan replikasi DNA, seperti CDKN2A, MCM2, MCM4, TOP2A, dan CDC20. Gen-gen tersebut diketahui berperan dalam proses proliferasi sel, pembelahan sel, serta pengaturan checkpoint siklus sel. Deregulasi ekspresi gen-gen tersebut dapat menyebabkan peningkatan aktivitas proliferatif dan ketidakstabilan genom yang merupakan karakteristik utama perkembangan kanker serviks. Oleh karena itu, gen-gen tersebut berpotensi digunakan sebagai kandidat biomarker untuk mendukung pemahaman mekanisme molekuler karsinogenesis serta sebagai target penelitian lebih lanjut dalam diagnosis atau terapi kanker serviks.

Kesimpulan

Berdasarkan hasil analisis transkriptomik pada dataset GSE9750, ditemukan sejumlah gen yang mengalami perubahan ekspresi secara signifikan antara sel serviks normal dan sel kanker serviks. Analisis DEG serta visualisasi melalui volcano plot dan heatmap menunjukkan adanya perbedaan pola ekspresi gen yang jelas antara kedua kelompok sampel. Hasil analisis Gene Ontology dan KEGG pathway enrichment menunjukkan bahwa gen-gen yang terderegulasi terutama terlibat dalam proses biologis yang berkaitan dengan siklus sel, replikasi DNA, pembelahan inti, serta segregasi kromosom, yang merupakan mekanisme penting dalam proliferasi sel kanker. Selain itu, jalur pensinyalan seperti PI3K-Akt signaling pathway juga teridentifikasi secara signifikan. Temuan ini menunjukkan bahwa deregulasi gen yang berkaitan dengan regulasi siklus sel dan proliferasi sel berperan penting dalam mekanisme molekuler karsinogenesis kanker serviks serta berpotensi menjadi kandidat biomarker untuk penelitian lebih lanjut.


