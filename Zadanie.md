# Klasy abstrakcyjne i dziedziczenie w Pythonie

## Opis zadania:
Twoim zadaniem jest zaimplementowanie hierarchii klas w języku Python, wykorzystując klasy abstrakcyjne i dziedziczenie.

### 1. Utwórz klasę abstrakcyjną `Base`, która będzie zawierała:
- Atrybuty `name` (nazwa) oraz `year` (rok urodzenia/stworzenia).
- Konstruktor (`__init__`) do inicjalizacji tych atrybutów.
- Abstrakcyjną metodę `info()`, która będzie musiała zostać zaimplementowana w klasach dziedziczących.

### 2. Utwórz klasę `Czlowiek`, która będzie dziedziczyć po klasie `Base`:
- Dodaj nowy atrybut `profession` (zawód).
- Zaimplementuj metodę `info()`, która zwróci informację w formacie: 
```shell
Człowiek: <imię>, Rok urodzenia: <rok>, Zawód: <zawód>
```

### 3. Utwórz klasę `Zwierze`, która również będzie dziedziczyć po `Base`:
- Dodaj nowy atrybut `species` (gatunek).
- Zaimplementuj metodę `info()`, która zwróci informację w formacie:
```shell
Zwierzę: <imię>, Rok urodzenia: <rok>, Gatunek: <gatunek>
```

### 4. Utwórz obiekty obu klas i uzupełnij ich atrybuty:
- `Czlowiek`: imię `"Jan Kowalski"`, rok urodzenia `1990`, zawód `"Inżynier"`.
- `Zwierze`: imię `"Reksio"`, rok urodzenia `2015`, gatunek `"Pies"`.

### 5. Wypisz informacje o utworzonych obiektach za pomocą metody `info()`.

---

## Rozwiązanie:

```python
from abc import ABC, abstractmethod

# Klasa abstrakcyjna
class Base(ABC):
  def __init__(self, name: str, year: int):
      self.name = name
      self.year = year

  @abstractmethod
  def info(self):
      pass

# Klasa Człowiek dziedzicząca po Base
class Czlowiek(Base):
  def __init__(self, name: str, year: int, profession: str):
      super().__init__(name, year)
      self.profession = profession  # Nowe pole - zawód

  def info(self):
      return f"Człowiek: {self.name}, Rok urodzenia: {self.year}, Zawód: {self.profession}"

# Klasa Zwierzę dziedzicząca po Base
class Zwierze(Base):
  def __init__(self, name: str, year: int, species: str):
      super().__init__(name, year)
      self.species = species  # Nowe pole - gatunek

  def info(self):
      return f"Zwierzę: {self.name}, Rok urodzenia: {self.year}, Gatunek: {self.species}"

# Tworzenie obiektów
czlowiek = Czlowiek(name="Jan Kowalski", year=1990, profession="Inżynier")
zwierze = Zwierze(name="Reksio", year=2015, species="Pies")

# Wypisywanie informacji
print(czlowiek.info())
print(zwierze.info())
