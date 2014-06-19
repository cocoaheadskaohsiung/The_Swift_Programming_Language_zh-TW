# 關於 Swift
~~~
IMPORTANT

This is a preliminary document for an API or technology in development. Apple is supplying this information to help you plan for the adoption of the technologies and programming interfaces described herein for use on Apple-branded products. This information is subject to change, and software implemented according to this document should be tested with final operating system software and final documentation. Newer versions of this document may be provided with future betas of the API or technology.
~~~

Swift 是一種新的程式語言，用於設計 iOS 和 OS X 應用。Swift 結合了 C 和 Objective-C 的優點，並且不受的 C 相容性限制。Swift 採用安全的程式設計​模式（Programming Patterns），並添加了很多新特性，這將使程式設計更簡單，更靈活，也更有趣。Swift 基於成熟及倍受喜愛的 Cocoa 和 Cocoa Touch frameworks（框架），是可以重新想像軟體開發是如何運作的契機。

Swift 的開發在許多年前就在進行了，Apple 藉由強化編譯器（compiler）、除錯器（debugger）及框架結構（framework infrastructure），以奠定 Swift 的基石。我們用 ARC（Automatic Reference Counting，自動引用計數）來簡化記憶體管理。我們在Foundation 和 Cocoa 的基礎上構建 framework stack（框架堆疊）並將其標準化。Objective-C 本身支援 block（區塊）、集合語法（collection literal）與模組（module），讓 framework 可以使用現代程式語言的技術，感謝過去奠定的基石，我們現在才能介紹用於未來 Apple 軟體開發的新語言。

Objective-C 開發者對 Swift 並不會感到陌生，Swift 採用了 Objective-C 的命名參數以及 dynamic object module（動態物件模型），可以無縫地對接到現有的 Cocoa framework，並且可以相容於 Objective-C 的程式碼。在此基礎之上，Swift 有許多新功能，並將語言在程序（procedural）及物件導向（object oriented）的部分做了結合。

Swift 對於初學者也很友善，它是第一個工業品質的系統程式設計語言，又具有腳本語言（script language）充滿表現力及和趣味的程式語言。它支援程式碼預覽（playground），這項創新的功能可以讓程式設計師不用編譯與執行應用程式，就能預覽 Swift 程式碼的執行結果。

Swift 將現代程式語言的精華和 Apple 工程師文化的智慧結合了起來。編譯器對效能進行最佳化，而程式語言對開發進行最佳化，兩者互不干擾，魚與熊掌兼得。Swift 既可以用於開發 “hello, world” 這樣的小程式，也可以用於開發一套完整的作業系統，所有的這些功能讓 Swift 對於開發者和 Apple 來說都是一項值得的投資。

用 Swift 設計 iOS 和 OS X 的應用將是一場美妙的體驗，Swift 之後也會不斷開發新功能與相容性，我們對 Swift 充滿信心，你還在等什麼！

Swift is a new programming language for iOS and OS X apps that builds on the best of C and Objective-C, without the constraints of C compatibility. Swift adopts safe programming patterns and adds modern features to make programming easier, more flexible, and more fun. Swift’s clean slate, backed by the mature and much-loved Cocoa and Cocoa Touch frameworks, is an opportunity to reimagine how software development works.

Swift has been years in the making. Apple laid the foundation for Swift by advancing our existing compiler, debugger, and framework infrastructure. We simplified memory management with Automatic Reference Counting (ARC). Our framework stack, built on the solid base of Foundation and Cocoa, has been modernized and standardized throughout. Objective-C itself has evolved to support blocks, collection literals, and modules, enabling framework adoption of modern language technologies without disruption. Thanks to this groundwork, we can now introduce a new language for the future of Apple software development.

Swift feels familiar to Objective-C developers. It adopts the readability of Objective-C’s named parameters and the power of Objective-C’s dynamic object model. It provides seamless access to existing Cocoa frameworks and mix-and-match interoperability with Objective-C code. Building from this common ground, Swift introduces many new features and unifies the procedural and object-oriented portions of the language.

Swift is friendly to new programmers. It is the first industrial-quality systems programming language that is as expressive and enjoyable as a scripting language. It supports playgrounds, an innovative feature that allows programmers to experiment with Swift code and see the results immediately, without the overhead of building and running an app.

Swift combines the best in modern language thinking with wisdom from the wider Apple engineering culture. The compiler is optimized for performance, and the language is optimized for development, without compromising on either. It’s designed to scale from “hello, world” to an entire operating system. All this makes Swift a sound future investment for developers and for Apple.

Swift is a fantastic way to write iOS and OS X apps, and will continue to evolve with new features and capabilities. Our goals for Swift are ambitious. We can’t wait to see what you create with it.
