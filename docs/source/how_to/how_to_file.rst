檔案處理
===============================

這個章節主要能夠讓你入門這個框架的基礎檔案處理。

對於函式庫，見 `函式庫文件 <https://ntut-xuan.github.io/LeistungsstarkesGameFramework/index.html>`_。



讀取檔案
-------------------------------

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
-------------------------------

基於這個框架是以 MV C++ 為基礎，故我們可以對其做檔案存取。

我們可以使用 ``ofstream`` 來寫入特定檔案。

對於更多詳細訊息，見 `https://cplusplus.com/reference/fstream/ofstream/ofstream/ <https://cplusplus.com/reference/fstream/ofstream/ofstream//>`_

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
