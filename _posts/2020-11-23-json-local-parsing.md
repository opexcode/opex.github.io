---
layout: post
fontsize: 10pt
title: Парсинг JSON-файла
tags: JSON
---

---

### Пример JSON-файла
```json
{
"friends": [
      {
        "id": 0,
        "name": "Pollard Snow"
      },
      {
        "id": 1,
        "name": "Schwartz Orr"
      },
      {
        "id": 2,
        "name": "Long Gill"
      }
    ]
}
```
Сначала отразим структуру JSON-файла, используя протокол `Decodable`:
```swift
struct Answer: Decodable {
  var friends: [Friends]
}

struct Friends: Decodable, Identifiable {
  var id: Int?
  var name: String?
}
```
Создаем класс который будет отвечать за парсинг:
```swift
class JSONParser: ObservableObject {
	
  @Published var json = [Friends]()
	
  init() {
    parse()
  }
	
  private func parse() {
	var d: Data?
	do {
	  d = try Data(contentsOf: URL(fileURLWithPath: Bundle.main.path(forResource: "data", 
	  ofType: "json")!))

	} catch {
	  print("Ошибка получения Data: \(error.localizedDescription)")
	}
	
	guard let data = d else {
	  print("Error...")
	  return
	}
	
	do {
	  let answer = try JSONDecoder().decode(Answer.self, from: data)
	  self.json = answer.friends
	} catch {
	  print("JSON decode failed: \(error.localizedDescription)")
	} 
  }
}
```
Пример использования:
```swift
struct ContentView: View {
  var fetch = JSONParser()

  var body: some View {
	List(fetch.json) { item in
	  Text(item.name!)
	}
  }
}
```

