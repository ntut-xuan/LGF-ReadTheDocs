修改 About
===============================
這個章節主要能夠讓你入門如何修改遊戲中的 About。

對於函式庫，見 `函式庫文件 <https://ntut-xuan.github.io/LeistungsstarkesGameFramework/index.html>`_。


如何修改
-------------------------------
目前的 About 在 ``/Source/Core/game.rc`` 內 `約 157-171 行的位置 <https://github.com/ntut-xuan/LeistungsstarkesGameFramework/blob/main/Source/Core/game.rc#L157-L171>`_。

你可以透過修改 ``LTEXT <文字> IDC_STATIC <x座標> <y座標> <寬度> <高度>`` 來設計你的 About。