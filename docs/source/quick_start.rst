快速入門
==========================================

在這份文件中，我會描述怎麼快速入門 LGF 框架。

.. note::
    我們建議使用 LGF 框架練習專案，來練習如何使用這個框架。


作業系統環境要求
---------------------

基於框架使用 `DirectX <https://zh.wikipedia.org/zh-tw/DirectX>`_，目前 LGF 僅能運行在 Windows 環境。

.. list-table:: 可用作業系統環境要求
    :header-rows: 1
    :widths: 50 50
    :align: center

    * - 作業系統
      - 能否正常運行專案
    * - Windows
      - 可正常運行
    * - Linux
      - 無法正常運行
    * - Mac OS
      - 無法正常運行


整合開發環境要求
---------------------

框架已被證實能夠在以下的整合開發環境（IDE）運行。

.. list-table:: 可用 IDE 列表
    :header-rows: 1
    :widths: 50 50
    :align: center

    * - IDE
      - 能否正常運行專案
    * - Visual Studio 2017
      - 可正常運行
    * - Intellij Rider
      - 可正常運行
    * - Visual Studio 2019
      - 未知
    * - Visual Studio 2022
      - 未知


安裝必要套件
---------------------

以 ``Visual Studio`` 為整合開發環境而言，安裝套件會需要 ``Visual Studio Installer`` 來幫助你安裝必須的套件，你需要準備好後進行以下要求的安裝。

在這份框架中，我們會需要以下的工具來建置 LGF 專案：

 -  Visual Studio 的「使用 C++ 的桌面開發」工作負載
 -  x86 與 x64 版 C++ MFC
 -  Windows 10 SDK

.. image:: https://camo.githubusercontent.com/479ab0431d283e1a03a2df0003e8deeecd28b1829283c0c7a96916aa2467b290/68747470733a2f2f692e696d6775722e636f6d2f7a786630636b792e706e67

當你完成安裝後，你就能夠開始嘗試建置專案。


嘗試建置專案
---------------------

當一切完成後，開啟框架練習專案的 ``game.sln``，檔案，接著你就可以使用「本機 Windows 偵錯工具」來嘗試建置專案。

.. image:: https://camo.githubusercontent.com/d6e78d01c032677c6c2cc91d81c1edcad500dcdb11090787635c631b06e16b40/68747470733a2f2f692e696d6775722e636f6d2f3250334973364a2e706e67

當你成功建置練習專案後，你應可以看到練習開始的畫面。若你使用的是無更改的專案，你應可以看到進度條與遊戲畫面。
