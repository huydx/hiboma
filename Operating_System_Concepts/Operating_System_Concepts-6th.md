# Operating System Conectps

## 5. THREADS

parallel, concurrency

 * 共有するもの
   * コードセグメント、データセグメント、ファイルテーブル
 * 共有しないもの
   * プログラムカウンタ、レジスタ、スタック

 * user thread
   * ユーザランドで実装するマルチスレッド。軽量
   * ブロックするシステムコール呼び出しで並行性が低下
   * Green threads
 * light weight process ( LWP)
 * kernel thread
   * カーネルで実装するスレッド。user thread に比べて重量
   * ブロッキングする場合にスケジューリング可能

## 5.2 Multithreading Models

マルチスレッドモデルの対比

 * ユーザランドで実装するスレッドの数とカーネルのスレッドの数で比較する
   * スケジューリング可能か否か
   * ブロックの有無

 * Many-To-One モデル ... `Green threads`
   * Solaris 2
   * parallel++ , concurrency--
   
```
     USER      KERNEL
   ---------+---------
    ~~~~~~> |
    ~~~~~~> |
    ~~~~~~> + ~~~~~~>
    ~~~~~~> |
    ~~~~~~> |
   ---------+---------
```   

 * One-To-One モデル
   * Windows NT, Windows 2000 OS/2
   * parallel++, concurrency++

```
     USER      KERNEL
   ---------+---------
    ~~~~~~> + ~~~~~~>
            |
    ~~~~~~> + ~~~~~~>
            |
    ~~~~~~> | ~~~~~~>
   ---------+---------
```   

 * Many-To-Many モデル
   * parallel++, concurrency++,
   * mu
   * Solaris 2, IRIX, HP-UX, Tru64 UNIX

```
     USER      KERNEL
   ---------+---------
    ~~~~~~> |
    ~~~~~~> + ~~~~~~>
    ~~~~~~> + ~~~~~~>
    ~~~~~~> + ~~~~~~>
    ~~~~~~> |
   ---------+---------
```

### misc

 * multithread と fork, exec
   * fork + exec するなら fork呼び出ししたスレッドだけ複製すると良い
   * fork だけなら 全スレッドを複製するのが良い
     * 使い分けできる API ある?

 * Cancellation
   * Asyncronous Cancellation
   * Deffered Cancellation
 
 * Signal Handling
 * Threads Pools
 * Thread-Specific Data

 * Pthread
   * POSXI standard IEEE 1003.1c
   * 仕様 である。実装 ではない。
 * Mach C-threads
 * Solaris 2 UI-threads

 * いろんなプラットフォームのスレッド実装
  * Solaris 2
  * Windows 2000
  * Linux 2.2 ~
  * Java Thread
    * スレッドをOS側でどのように扱うかは、OSの実装依存
