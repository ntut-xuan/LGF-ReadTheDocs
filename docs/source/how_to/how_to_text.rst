文字處理
===========================

這個章節主要能夠讓你入門這個框架的基礎文字處理。

對於函式庫，見 `函式庫文件 <https://ntut-xuan.github.io/LeistungsstarkesGameFramework/index.html>`_。


呈現文字到畫面上
---------------------------

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
---------------------------

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

