# 關於 Swift

    重要注意事項：
        本份文件為初步描述 Swift 相關技術的開發用文件。 蘋果公司提供此份文件來協助您在蘋果官方產品上應用此技術。
        本份文件將在最後釋出的作業系統上進行驗證與測試，而 Swift 語言將依據此份規格進行實作，過程中如有任何變更與修正將會更新此份文件。
        本文件後續更新版本中將可能包含一些尚在測試中的規格或 API。

Swift 是一種用於開發 iOS 和 OS X 應用程式的新程式語言。它結合了 C 和 Objective-C 的優點，並且改善了 C 相容性限制的缺點。它採用了許多安全的程式設計​模式（Programming Patterns），並添加了很多新特性，這些將使程式設計更簡單、靈活，也更有趣。Swift 基於成熟及倍受喜愛的 Cocoa 和 Cocoa Touch 程式框架（Frameworks）。學習 Swift 將可以讓您重新回味軟體開發是如何運作。

Swift 的開發已經進行許多年了，Apple 藉由強化編譯器（compiler）、除錯器（debugger）及框架結構（framework infrastructure），以奠定 Swift 的基石。我們用 ARC（Automatic Reference Counting，自動引用計數）來簡化記憶體管理。我們在Foundation 和 Cocoa 的基礎上構建 framework stack（框架堆疊）並將其標準化。Objective-C 本身支援 block（區塊）、集合語法（collection literal）與模組（module），讓 framework 可以使用現代程式語言的技術，感謝過去奠定的基石，我們現在才能介紹用於未來 Apple 軟體開發的新語言。

Swift has been years in the making. Apple laid the foundation for Swift by advancing our existing compiler, debugger, and framework infrastructure. We simplified memory management with Automatic Reference Counting (ARC). Our framework stack, built on the solid base of Foundation and Cocoa, has been modernized and standardized throughout. Objective-C itself has evolved to support blocks, collection literals, and modules, enabling framework adoption of modern language technologies without disruption. Thanks to this groundwork, we can now introduce a new language for the future of Apple software development.


Objective-C 開發者對 Swift 並不會感到陌生，Swift 採用了 Objective-C 的命名參數以及 dynamic object module（動態物件模型），可以無縫地對接到現有的 Cocoa framework，並且可以相容於 Objective-C 的程式碼。在此基礎之上，Swift 有許多新功能，並將語言在程序（procedural）及物件導向（object oriented）的部分做了結合。

Swift 對於初學者也很友善，它是第一個工業品質的系統程式設計語言，又具有腳本語言（script language）充滿表現力及和趣味的程式語言。它支援程式碼預覽（playground），這項創新的功能可以讓程式設計師不用編譯與執行應用程式，就能預覽 Swift 程式碼的執行結果。

Swift 將現代程式語言的精華和 Apple 工程師文化的智慧結合了起來。編譯器對效能進行最佳化，而程式語言對開發進行最佳化，兩者互不干擾，魚與熊掌兼得。Swift 既可以用於開發 “hello, world” 這樣的小程式，也可以用於開發一套完整的作業系統，所有的這些功能讓 Swift 對於開發者和 Apple 來說都是一項值得的投資。

用 Swift 設計 iOS 和 OS X 的應用將是一場美妙的體驗，Swift 之後也會不斷開發新功能與相容性，我們對 Swift 充滿信心，你還在等什麼！

Swift feels familiar to Objective-C developers. It adopts the readability of Objective-C’s named parameters and the power of Objective-C’s dynamic object model. It provides seamless access to existing Cocoa frameworks and mix-and-match interoperability with Objective-C code. Building from this common ground, Swift introduces many new features and unifies the procedural and object-oriented portions of the language.

Swift is friendly to new programmers. It is the first industrial-quality systems programming language that is as expressive and enjoyable as a scripting language. It supports playgrounds, an innovative feature that allows programmers to experiment with Swift code and see the results immediately, without the overhead of building and running an app.

Swift combines the best in modern language thinking with wisdom from the wider Apple engineering culture. The compiler is optimized for performance, and the language is optimized for development, without compromising on either. It’s designed to scale from “hello, world” to an entire operating system. All this makes Swift a sound future investment for developers and for Apple.

Swift is a fantastic way to write iOS and OS X apps, and will continue to evolve with new features and capabilities. Our goals for Swift are ambitious. We can’t wait to see what you create with it.
