# AriQuantum 🌌

**Простая библиотека для симуляции квантовых вычислений с интуитивным интерфейсом.**  
Идеально подходит для студентов и новичков в квантовых вычислениях — никаких сложных зависимостей и шумовых моделей, только базовые операции и визуализация.

[![PyPI version](https://badge.fury.io/py/ariquantum.svg)](https://badge.fury.io/py/ariquantum)
[![PyPI Downloads](https://static.pepy.tech/personalized-badge/ariquantum?period=total&units=INTERNATIONAL_SYSTEM&left_color=BLACK&right_color=GREEN&left_text=downloads)](https://pepy.tech/projects/ariquantum)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)


---

## Установка

Требуется Python 3.9+ и `numpy`:
```bash
pip install ariquantum
```

---

## Быстрый старт

### 1. Работа с отдельными кубитами
```python
from ariquantum.qubit import Qubit

# Создание кубитов в разных состояниях
q0 = Qubit('0')
q_plus = Qubit('+')

# Вывод в бра-кет нотации Дирака
print(q0.as_bracket_string())     # |0⟩
print(q_plus.as_bracket_string()) # 0.70711|0⟩ + 0.70711|1⟩
```

### 2. Квантовые схемы и визуализация
```python
from ariquantum.quantum_register import QuantumRegister

qr = QuantumRegister(2)  # 2-кубитный регистр

# Применение гейтов: H на 0-й кубит, CX между 0 и 1
qr.h(0)
qr.cx(0, 1)

# Вывод состояния и схемы
print(qr.as_bracket_string())
# 0.7071|00⟩ + 0.7071|11⟩

qr.draw_circuit()
#       ┌───┐       
# q0 : ─│ H │───●─── :
#       └───┘   │
#             ┌─┴─┐
# q1 : ───────│ X │─ :
#             └───┘
```

### 3. Измерения
```python
qr.measure(qubits=[0, 1])  # Отложенное измерение
print(qr.get_counts(shots=100))
# Пример вывода: {'11': 53, '00': 47}
```

---

## Основные возможности
- **Гибкое управление**: Работа с отдельными кубитами и квантовыми регистрами.
- **Визуализация схем**: Автоматическая отрисовка квантовых цепей в ASCII-графике.
- **Бра-кет нотация**: Человекочитаемое представление состояний (например, `0.7|00⟩ + 0.7|11⟩`).
- **Измерения**: Поддержка отложенных измерений с настраиваемым количеством прогонов (shots).

---

## Структура проекта
```
ariquantum/
├── __init__.py
├── build_operator.py    # Построение операторов для системы кубитов
├── exceptions.py        # Специализированные исключения
├── helpers.py           # Вспомогательные функции
├── quantum_register.py  # Ядро: управление квантовыми регистрами
├── qubit.py             # Класс для работы с отдельными кубитами
└── visualization.py     # Визуализация состояний и схем
```

---

## Лицензия
Распространяется под лицензией **[MIT](https://opensource.org/licenses/MIT)**.

---

## Поддержка
Вопросы и предложения можно отправлять:
- [Issues на GitHub](https://github.com/ariquantum)
- Email: arimshcherbakov@gmail.com
- Telegram: [@ArimShcherbakov](https://t.me/ArimShcherbakov)

English version: [README.md](README.md)
