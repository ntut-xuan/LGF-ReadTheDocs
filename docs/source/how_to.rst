How-To
===========================

這個章節主要能夠讓你入門這個框架的基礎操作。

對於函式庫，見 `函式庫文件 <https://ntut-xuan.github.io/LeistungsstarkesGameFramework/index.html>`_。


圖片處理
---------------------------

讀取一張圖片
~~~~~~~~~~~~~~~~~~~~~~~~~~~

我們可以使用以下的方式來讀取一張圖片、設定左上角座標並呈現它。

額外注意 ``LoadBitmap()`` 的第二個參數為一個 ``RGB``，代表過濾這張圖片的某特定顏色。

.. code-block:: C++

    CMovingBitmap bitmap;

    // -- onInit() function --

    bitmap.LoadBitmap("RES/bitmap.bmp", RGB(255, 255, 255));
    bitmap.SetTopLeft(0, 0);

    // -- onShow() function --

    bitmap.ShowBitmap();


讀取多張圖片
~~~~~~~~~~~~~~~~~~~~~~~~~~~

我們可以使用以下的方式來讀取多張圖片、設定左上角座標並呈現它。

額外注意 ``LoadBitmap()`` 的第二個參數為一個 ``RGB``，代表過濾的顏色。

透過設置這個參數，它將過濾所有圖片的特定顏色。

.. code-block:: C++

    CMovingBitmap bitmap;

    // -- onInit() function --

    bitmap.LoadBitmap({"RES/bitmap.bmp", "RES/bitmap2.bmp"}, RGB(255, 255, 255));
    bitmap.SetTopLeft(0, 0);

    // -- onShow() function --

    bitmap.ShowBitmap();


設定圖片為循環動畫
~~~~~~~~~~~~~~~~~~~~~~~~~

LGF 支援你將圖片設定為循環動畫，可以使用 ``SetAnimation(int time, bool once)`` 來設置。

.. code-block:: C++

    CMovingBitmap bitmap;

    // -- onInit() function --

    bitmap.LoadBitmap({"RES/bitmap.bmp", "RES/bitmap2.bmp"}, RGB(255, 255, 255));
    bitmap.SetTopLeft(0, 0);
    bitmap.SetAnimation(1000, false);

    // -- onShow() function --

    bitmap.ShowBitmap();

透過設置 ``once`` 參數為 ``false`` 後，動畫就會在 ``ShowBitmap()`` 時無限循環。


設定圖片為單次動畫
~~~~~~~~~~~~~~~~~~~~~~~~~

LGF 支援你將圖片設定為單次動畫，可以使用 ``SetAnimation(int time, bool once)`` 來設置。

.. code-block:: C++

    CMovingBitmap bitmap;

    // -- onInit() function --

    bitmap.LoadBitmap({"RES/bitmap.bmp", "RES/bitmap2.bmp"}, RGB(255, 255, 255));
    bitmap.SetTopLeft(0, 0);
    bitmap.SetAnimation(1000, true);

    // -- onMove() function
    bitmap.ToggleAnimation();

    // -- onShow() function --

    bitmap.ShowBitmap();

透過設置 ``once`` 參數為 ``true`` 後，動畫不會自己啟動，等到 ``ToggleAnimation()`` 呼叫後啟動一次。

每次 ``ShowBitmap()`` 時，它固定會呈現一幀，直到沒有幀可以呈現時，停止動畫。


切換幀
~~~~~~~~~~~~~~~~~~~~~~~~

若你的 `CMovingBitmap <https://ntut-xuan.github.io/LeistungsstarkesGameFramework/classgame__framework_1_1_c_moving_bitmap.html>`_ 具有許多的幀，你可以選擇要呈現哪一張。

.. code-block:: C++

    CMovingBitmap bitmap;

    // -- onInit() function --

    bitmap.LoadBitmap({"RES/bitmap.bmp", "RES/bitmap2.bmp"}, RGB(255, 255, 255));
    bitmap.SetTopLeft(0, 0);
    bitmap.SetAnimation(1000, true);

    // -- onMove() function
    bitmap.SetFrameIndexOfBitmap(1); // Show the second image.

    // -- onShow() function --

    bitmap.ShowBitmap();

透過 ``SetFrameIndexOfBitmap()`` 來設定要呈現哪一張圖片。

以上述的程式碼為例，這會讓 ``bitmap`` 呈現第二張圖片。


重疊確認
~~~~~~~~~~~~~~~~~~~~~~~~

在 ``v1.1.0`` 以後的版本的 LGF，支援使用者使用 ``CMovingBitmap::IsOverlap`` 函數來取得兩張圖片是否重疊。

.. code-block:: C++

    CMovingBitmap bitmap1;
    CMovingBitmap bitmap2;

    // -- onInit() function --

    bitmap1.LoadBitmap({"RES/bitmap.bmp", RGB(255, 255, 255));
    bitmap1.SetTopLeft(0, 0);

    bitmap2.LoadBitmap({"RES/bitmap2.bmp", RGB(255, 255, 255));
    bitmap2.SetTopLeft(0, 0);

    // -- onMove() function

    /* It should return two images is overlap or not with boolean. */
    bool isOverlap = CMovingBitmap::IsOverlap(bitmap1, bitmap2); 
    
    // -- onShow() function --

    bitmap1.ShowBitmap();
    bitmap2.ShowBitmap();


文字處理
---------------------------


呈現文字到畫面上
~~~~~~~~~~~~~~~~~~~~~~~~~~~

LGF 支援你呈現文字到畫面上。

.. warning::
    呈現文字到畫面上會占用 ``CDC``，故必須要在圖片呈現完成後，占用 ``CDC`` 來呈現文字，所以文字必定會在最上層。


.. code-block:: C++
    
    // -- onShow() function --

    /*
     *
     * Show some images here.
     *
     */

    CDC *pDC = CDDraw::GetBackCDC();
    CTextDraw::Print(pDC, 300, 600, "Some text here.");

上面的程式碼會將 ``Some text here`` 這個字串印到座標 ``(300, 600)`` 上。


修改字體屬性
~~~~~~~~~~~~~~~~~~~~~~~~~~~

LGF 支援你修改印出的字體屬性，並套用到現在的 CDC 上。

.. warning::
    呈現文字到畫面上會占用 ``CDC``，故必須要在圖片呈現完成後，占用 ``CDC`` 來呈現文字，所以文字必定會在最上層。


.. code-block:: C++
    
    // -- onShow() function --

    /*
     *
     * Show some images here.
     *
     */

    CDC *pDC = CDDraw::GetBackCDC();

    ChangeFontLog(pDC, 15, "微軟正黑體", RGB(0, 0, 0), 500);

    CTextDraw::Print(pDC, 300, 600, "Print the text with size 15, font 微軟正黑體, black color and 500 weight here.")


檔案處理
-------------------------------

讀取檔案
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

基於這個框架是以 MV C++ 為基礎，故我們可以對其做檔案存取。

我們可以使用 ``ifstream`` 來讀取特定檔案，並存取特定檔案的值。

對於更多詳細訊息，見 `https://cplusplus.com/reference/fstream/ifstream/ifstream/ <https://cplusplus.com/reference/fstream/ifstream/ifstream/>`_

.. code-block:: text
    :caption: map/Random.map

    0 1 1 1 0
    0 1 1 1 0
    0 1 1 1 0
    0 0 0 0 0
    1 1 1 1 1

.. code-block:: c++
    :caption: mygame_run.cpp

    /* Assume we have a file map/Random.map */
    #include <fstream>

    // -- OnInit() function --
    ifstream ifs("map/Random.map");

    int map[5][5];

    for(int i = 0; i < 5; i++){
        for(int j = 0; j < 5; j++){
            ifs >> map[i][j];
        }
    }

    ifs.close();


寫入檔案
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

基於這個框架是以 MV C++ 為基礎，故我們可以對其做檔案存取。

我們可以使用 ``ofstream`` 來寫入特定檔案。

對於更多詳細訊息，見 `https://cplusplus.com/reference/fstream/ifstream/ifstream/ <https://cplusplus.com/reference/fstream/ifstream/ifstream/>`_

.. warning::
    請記得在寫入完成後，使用 ``close()`` 成員來關閉 ``ofstream``，以確保資料能夠正確寫入。

.. code-block:: text
    :caption: map/Random.map

    0 1 1 1 0
    0 1 1 1 0
    0 1 1 1 0
    0 0 0 0 0
    1 1 1 1 1

.. code-block:: c++
    :caption: mygame_run.cpp

    /* Assume we have a file map/Random.map */
    #include <fstream>

    // -- OnInit() function --
    ofstream ofs("map/Random.map");

    int map[5][5] = {
        {0, 1, 1, 1, 0},
        {0, 1, 1, 1, 0},
        {0, 1, 1, 1, 0},
        {0, 0, 0, 0, 0},
        {1, 1, 1, 1, 1}
    };

    for(int i = 0; i < 5; i++){
        for(int j = 0; j < 5; j++){
            ofs << map[i][j];
        }
    }

    ofs.close();
