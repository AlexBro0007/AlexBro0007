import numpy as np
import matplotlib.pyplot as plt

# Установим длину каждого этапа
years_per_phase = 20  # Среднее количество лет на каждую фазу
total_cycle_length = 4 * years_per_phase  # Общая длина одного полного цикла

# Названия фаз в теории Штрауса-Хоу
phases = ["Кризис", "Высокая фаза", "Пробуждение", "Распад"]

# Сгенерируем временные метки для цикла
years = np.arange(0, total_cycle_length + 1)

# Создадим массив значений, соответствующий фазам
phase_values = np.zeros_like(years)
for i in range(4):
    phase_values[i*years_per_phase:(i+1)*years_per_phase] = i+1

# Установим начальный год для кризиса
start_year = 1929
real_years = np.arange(start_year, start_year + total_cycle_length + 1)

# Визуализируем фазы на реальной временной шкале
plt.figure(figsize=(10, 6))
plt.plot(real_years, phase_values, drawstyle='steps-post', color='b', label="Фазы цикла Штрауса-Хоу")
plt.fill_between(real_years, phase_values, step="post", alpha=0.3)

# Добавим подписи для фаз
for i, phase in enumerate(phases):
    mid_point = start_year + (i * years_per_phase) + (years_per_phase / 2)
    plt.text(mid_point, i+1, phase, ha='center', va='bottom', fontsize=12, color='black')

# Оформление графика
plt.title("Циклы Штрауса-Хоу на реальной временной шкале", fontsize=16)
plt.xlabel("Год", fontsize=12)
plt.ylabel("Фазы", fontsize=12)
plt.yticks([1, 2, 3, 4], phases)
plt.grid(True)
plt.tight_layout()

# Показать график
plt.show()
