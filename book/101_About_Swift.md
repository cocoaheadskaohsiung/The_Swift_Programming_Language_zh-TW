# 關於 Swift

    重要注意事項：
        本份文件為初步描述 Swift 相關技術的開發用文件。蘋果公司提供此份文件來協助您在蘋果官方產品上應用此技術。本份文件將在最後釋出的作業系統上進行驗證與測試，而 Swift 語言將依據此份規格進行實作，過程中如有任何變更與修正將會更新此份文件。
        本文件後續更新版本中將可能包含一些尚在測試中的規格或 API。

Swift 是一種用於開發 iOS 和 OS X 應用程式的新程式語言。它結合了 C 和 Objective-C 的優點，並且改善了 C 相容性限制的缺點。它採用了許多安全的程式設計​模式（Programming Patterns），並添加了很多新特性，這些將使程式設計更簡單、靈活，也更有趣。Swift 基於成熟及倍受喜愛的 Cocoa 和 Cocoa Touch 程式框架（Frameworks）。學習 Swift 將可以讓您重新回味軟體開發是如何運作。

Swift 的開發已經進行許多年了。蘋果公司在已經發展成熟的編譯器（compiler）、除錯器（debugger）及系統資訊框架（framework infrastructure）基礎上開發 Swift。我們用物件記憶體自動回收管理技術（ARC，Automatic Reference Counting）來簡化記憶體管理。我們有基於 Foundation 和 Cocoa 的基礎上先進而且已經成為標準的系統結構堆疊（framework stack）。本身支援 區塊（block）、集合迭代（collection literal）與模組化（module）的 Objective-C，讓新的語言不需額外的努力就可以跟現代程式語言的技術接軌。感謝過去的所有努力，我們現在才能介紹用於未來 Apple 軟體開發的新語言。

> **todo** 翻譯中

Objective-C 開發者應該會對 Swift 這個新程式語言非常熟悉。Swift 與 Objective-C 在參數命名上有同樣的可閱讀性，在動態物件模組（dynamic object module）也有相同的威力。可以讓您無縫接軌到現有的 Cocoa （frameworks），並且可以相容於 Objective-C 的程式碼。在此基礎之上，Swift 有許多新功能，並將語言在程序（procedural）及物件導向（object oriented）的部分做了結合。

Swift feels familiar to Objective-C developers. It adopts the readability of Objective-C’s named parameters and the power of Objective-C’s dynamic object model. It provides seamless access to existing Cocoa frameworks and mix-and-match interoperability with Objective-C code. Building from this common ground, Swift introduces many new features and unifies the procedural and object-oriented portions of the language.

Swift 對於初學者也很友善，它是第一個工業品質的系統程式設計語言，又具有腳本語言（script language）充滿表現力及和趣味的程式語言。它支援程式碼預覽（playground），這項創新的功能可以讓程式設計師不用編譯與執行應用程式，就能預覽 Swift 程式碼的執行結果。

Swift 將現代程式語言的精華和 Apple 工程師文化的智慧結合了起來。編譯器對效能進行最佳化，而程式語言對開發進行最佳化，兩者互不干擾，魚與熊掌兼得。Swift 既可以用於開發 “hello, world” 這樣的小程式，也可以用於開發一套完整的作業系統，所有的這些功能讓 Swift 對於開發者和 Apple 來說都是一項值得的投資。

用 Swift 設計 iOS 和 OS X 的應用將是一場美妙的體驗，Swift 之後也會不斷開發新功能與相容性，我們對 Swift 充滿信心，你還在等什麼！