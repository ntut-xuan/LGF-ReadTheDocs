檔案架構
=====================

從 ``v1.0.0`` 開始，LGF 檔案架構主要如下。


資料夾結構樹
---------------------

.. _directory-tree-label: 
.. code-block:: rst

    ├── Library/
    │   ├── gameutil.h
    │   ├── gameutil.cpp
    │   ├── gamecore.h
    │   └── gamecore.cpp
    ├── Core/
    │   └── Some core file...
    └── Game/
        ├── config.h
        ├── mygame.h
        ├── mygame_initialize.cpp
        ├── mygame_run.cpp
        └── mygame_over.cpp

以下，我們會一一介紹每個資料夾的職責，以及它們該做的事情。


Game 資料夾
---------------------

在 ``Game/`` 資料夾中， ``mygame_initialize.cpp``、``mygame_run.cpp`` 與 ``mygame_over.cpp`` 主要分配了遊戲中初始、運行過程與結束的任務。
這些檔案的主要實作了 ``mygame.h`` 內 ``CGameStateInit``、``CGameStateRun`` 與 ``CGameStateOver`` 的函式。
在實作遊戲中，我們可以在這三個檔案中，描述遊戲如何顯示畫面（``OnShow()``）、鍵盤與滑鼠事件（``onKeyDown()``）以及常駐事件（``onMove()``）等，見 :doc:`cgamestate_group`。

額外，我們還有一個 ``config.h``，用於設定遊戲的參數。


Library 資料夾
---------------------

在 ``Library/`` 資料夾中，``gameutil`` 提供了製作遊戲時必要的工具，例如 ``CMovingBitmap`` 與 ``CTextDraw`` 等類別。
而 ``gamecore`` 提供了 ``gameutil`` 有關遊戲核心的類別，可以大概看一下，但實際上設計遊戲時不會用到。

.. warning::
    我們強烈建議使用者不去更動 ``Library/`` 內部的東西，因為隨著框架更新新版本，你可能會讓原本更動的修正遺失。

Core 資料夾
---------------------

在 ``Core/`` 資料夾中，我們省略了這個部分的介紹。
基於 ``Core/`` 資料夾內主要描述了使用 ``MFC`` 製作的類別，使得遊戲能夠正常運作，故我們跳過了這個過程。

.. warning::
    我們強烈建議使用者不去更動 ``Core/`` 內部的東西，因為隨著框架更新新版本，你可能會讓原本更動的修正遺失。

    以及基於這邊的程式都是與 ``MFC`` 的溝通，改動這邊的東西可能會導致軟體不穩定，若不知道自己在做什麼，請不要變更這邊的程式。
