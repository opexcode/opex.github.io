---
layout: post
title: SwiftUI основы
tags: swift SwiftUI
---

---

### Элементы интерфейса
```swift
// TabView 
TabView {

    Text("First View")
        .font(.title)
        .tabItem({
            Image(systemName: "circle")
            Text("First")
        })
        .tag(0)
        
    Text("Second View")
        .font(.title)
        .tabItem(VStack {
            Image("second")
            Text("Second")
        })
        .tag(1)
}
```

### Основные операции
```swift
// Цикл ForEach
@State var fruits = ["apple", "orange", "ananas"]

ForEach(fruits, id: \.self) { data in
	Text(data)
}

// Нарисовать border вокруг view
.overlay(
        RoundedRectangle(cornerRadius: 16)
            .stroke(Color.blue, lineWidth: 4)
    )
```
