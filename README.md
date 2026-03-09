graph TD
    %% 階段 0
    subgraph Stage0 [0. 啟用前滿足條件]
        A[PK81501 / K30031 Stop] --&gt; B[TIC30001 Man 100% / PIC30002A/B Man 0%]
        B --&gt; C[YV30089 open / YV30092 open]
        C --&gt; D[其餘 YV/TV/PV 關閉與手動]
    end

    Stage0 --&gt; Stage1

    %% 階段 1
    subgraph Stage1 [1. 抽真空]
        E[PV30120 Man 100% &amp; K30031 Run] --&gt; F{壓力監測}
        F -- &quot;PI30087/PIC30002/PI30141 &lt; 120 torr&quot; --&gt; G[PV30120/YV30089/YV30092 Close]
        G --&gt; H[K30031 Stop]
    end

    Stage1 --&gt; Stage2

    %% 階段 2
    subgraph Stage2 [2. 持壓測試]
        I[持壓計時 30 min] --&gt; J{結果確認}
        J -- 成功 --&gt; K[進入下階段 3-2]
        J -- 不成功 --&gt; L[程序取消 3-1 &amp; 排除問題]
    end
