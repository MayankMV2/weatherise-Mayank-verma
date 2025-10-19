## 🔄 Before & After Code Transformations

### Example 1 – Strengthened Error Management  
**Previous:**

reply = requests.get(url)
info = reply.json()
return info

**Weakness:** No exception handling caused application crashes under network failure conditions.

**Revised:**
try:
reply = requests.get(url)
reply.raise_for_status()
info = reply.json()
return info
except Exception as err:
print(f"Unable to fetch weather data: {err}")
return None

**Effect:** Robust handling of network errors with informative feedback.

---

### Example 2 – Enhancing User Interaction During Plotting  
**Previous:**

plt.show()

**Challenge:** The program waits indefinitely for the plot window to close before continuing.

**Updated:**
plt.show()
plt.pause(0.1)
plt.close(fig)
plt.ioff()

**Benefit:** The plot displays efficiently without blocking the program, allowing instant menu response.

---

### Example 3 – Improved Plot Presentation  
**Previous:**
plt.plot(days_list, temps)
plt.show()

**Improvement:**
ax.plot(days_list, max_temps, color='orange', marker='s', linestyle='-', label='Max Temp (°C)')
ax.plot(days_list, min_temps, color='teal', marker='o', linestyle='--', label='Min Temp (°C)')
ax.set_title("Temperature Trend Overview")
ax.set_xlabel("Date")
ax.set_ylabel("Temperature (°C)")
ax.legend()
plt.grid(True)
plt.show()

**Result:** Clearer visualization with distinct styling, labels, and legends for better interpretation.
