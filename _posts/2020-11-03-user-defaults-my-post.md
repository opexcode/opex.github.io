---
layout: post
title: Сохраняем данные в UserDefaults
tags: swift UserDefaults
---

Используем UserDefaults для сохранения данных приложения.

---

## Строковый массив

Сохранить массив
```swift
let array = ["horse", "cow", "camel", "sheep", "goat"]

let defaults = UserDefaults.standard
defaults.set(array, forKey: "SavedStringArray")
```
Извлечь массив
```swift
let defaults = UserDefaults.standard
let myarray = defaults.stringArray(forKey: "SavedStringArray") ?? [String]()
```

## Массив Int

Сохранить массив
```swift
let array = [15, 33, 36, 723, 77, 4]

let defaults = UserDefaults.standard
defaults.set(array, forKey: "SavedIntArray")
```
Извлечь массив
```swift
let defaults = UserDefaults.standard
let array = defaults.array(forKey: "SavedIntArray")  as? [Int] ?? [Int]()
```
## Массив Bool

Сохранить массив
```swift
let array = [true, true, false, true, false]

let defaults = UserDefaults.standard
defaults.set(array, forKey: "SavedBoolArray")
```
Извлечь массив
```swift
let defaults = UserDefaults.standard
let array = defaults.array(forKey: "SavedBoolArray")  as? [Bool] ?? [Bool]()
```
## Дата время

Сохранить массив
```swift
let array = [Date(), Date(), Date(), Date()]

let defaults = UserDefaults.standard
defaults.set(array, forKey: "SavedDateArray")
```
Извлечь массив
```swift
let defaults = UserDefaults.standard
let array = defaults.array(forKey: "SavedDateArray")  as? [Date] ?? [Date]()
```