# VK

# 🚀 Операция "Push to Offer": 5-дневный Java-рейд в VK (MidSprint)

**Цель:** Успешно пройти техническое собеседование на позицию Java Backend Developer (MidSprint / Middle) в команду Дзена / Балансеров VK.
**Девиз:** Рассуждай вслух, пиши чистый код, думай о граничных случаях.

---

## 📜 Правила рейда
- [x] Режим 2/2/2/2: Делим день на блоки по 2 часа с перерывами по 30 минут.
- [x] Пишем код руками: если за 20 минут нет идеи → берем подсказку, если за 35 минут не решил → смотрим решение и переписываем его через 2 часа.
- [x] Говорим вслух: проговариваем ход мыслей, как на реальном лайв-кодинге.
- [x] Никаких хаков типа `AbstractList`: пишем читаемый, production-ready код.

---

## 📅 День 1: Фундамент алгоритмов + Java Core (Collections & JMM)
*Статус: ✅ ЗАВЕРШЕНО*
- [x] **Алгоритмы (Two Pointers, HashMap):**
  - [x] [1. Two Sum](https://leetcode.com/problems/two-sum/)
  - [x] [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)
  - [x] [15. 3Sum](https://leetcode.com/problems/3sum/) *(Разобрали дедупликацию указателями вместо HashSet)*
  - [x] [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/) *(Разобрали edge cases и `i < j` во внутренних циклах)*
- [x] **Java Core:**
  - [x] HashMap под капотом (treeify threshold, resize, коллизии).
  - [x] ConcurrentHashMap (CAS + synchronized на бакете, почему null запрещен).
  - [x] Контракт `equals` / `hashCode` (что будет, если hashCode возвращает константу или random).
- [x] **Многопоточность (JMM):**
  - [x] `volatile` (видимость + happens-before, но НЕ атомарность `++`).
  - [x] `AtomicLong` (CAS, spin loop) vs `LongAdder` (массив ячеек `Cell[]`, выигрыш при high contention).

---

## 📅 День 2: Продвинутые алгоритмы + Spring & Concurrency
*Статус: 🔄 В ПРОЦЕССЕ*
- [ ] **Алгоритмы (Sliding Window, Linked List):**
  - [ ] [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) *(Алгоритм Кадане, O(N))*
  - [ ] [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) *(Должен писать с закрытыми глазами)*
  - [ ] [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) *(Fast & Slow pointers / Черепаха и Заяц)*
  - [ ] [424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/) *(Sliding Window, Medium)*
- [ ] **Spring Framework:**
  - [ ] `@Transactional`: как работает прокси (JDK Dynamic vs CGLIB), ловушка self-invocation, Propagation (`REQUIRED` vs `REQUIRES_NEW`).
  - [ ] Жизненный цикл бина: Instantiation → Populate Properties → `@PostConstruct` → Ready → `@PreDestroy`.
- [ ] **Concurrency (Java 21):**
  - [ ] Virtual Threads vs Platform Threads: почему идеальны для I/O-bound и плохи для CPU-bound.
  - [ ] Pinning (прикрепление): почему `synchronized` блокирует carrier-поток и как это исправить (`ReentrantLock`).

---

## 📅 День 3: Базы данных (PostgreSQL) + Kafka & Микросервисы
*Статус: ⏳ ОЖИДАЕТ*
- [ ] **Алгоритмы (Trees & Graphs BFS/DFS):**
  - [ ] [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) *(BFS через Queue)*
  - [ ] [200. Number of Islands](https://leetcode.com/problems/number-of-islands/) *(DFS/BFS на матрице, топ-1 для бэкенда)*
  - [ ] [994. Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) *(Multi-source BFS)*
- [ ] **Базы данных (PostgreSQL):**
  - [ ] MVCC: как работает (старые версии строк, читатель не блокирует писателя).
  - [ ] WAL (Write-Ahead Logging): гарантия Durability (D из ACID).
  - [ ] Индексы: почему B-Tree (диапазоны, сортировка), а не Hash (только `=`). Правило левого префикса.
  - [ ] Проблема N+1 и её решение (`@EntityGraph`, `JOIN FETCH`).
- [ ] **Kafka и распределённые системы:**
  - [ ] Гарантии доставки: на практике `at-least-once` + идемпотентный консюмер.
  - [ ] Идемпотентность: таблица `processed_events` с `event_id UUID PRIMARY KEY` + `ON CONFLICT DO NOTHING` в одной транзакции.
  - [ ] Saga: оркестрация vs хореография, компенсирующие транзакции.

---

## 📅 День 4: System Design, Тестирование и Инфраструктура
*Статус: ⏳ ОЖИДАЕТ*
- [ ] **Алгоритмы (Mock Contest):**
  - [ ] Решить 3 случайные задачи из пройденных за 45 минут с таймером и проговариванием вслух.
- [ ] **Тестирование:**
  - [ ] Почему **Testcontainers** лучше H2? (Реальный диалект PostgreSQL, честный интеграционный тест).
  - [ ] Разница `@Mock` (полная заглушка) и `@Spy` (реальный объект с мокингом отдельных методов).
- [ ] **System Design (База):**
  - [ ] Rate Limiter: Token Bucket / Sliding Window Log, хранение в Redis с TTL.
  - [ ] Load Balancer: алгоритмы (Round Robin, Least Connections), Health checks.
- [ ] **Docker / Kubernetes:**
  - [ ] Multi-stage build (уменьшение размера образа).
  - [ ] Liveness probe (перезагрузить под, если завис) vs Readiness probe (убрать из балансировки, если не готов).

---

## 📅 День 5: Полировка, повторение и Soft Skills
*Статус: ⏳ ОЖИДАЕТ*
- [ ] **Работа над ошибками:**
  - [ ] Перерешать задачи, которые не получились в Дни 1-4, без подсказок.
- [ ] **Подготовка рассказов по проекту (STAR):**
  - [ ] Smart Fridge API: почему RabbitMQ, а не Kafka? (Contract-first, HATEOAS).
  - [ ] Java Concurrency Labs: как добился ускорения в 3 раза? (Разбиение на подзадачи, JIT warm-up, work-stealing).
  - [ ] Text File Indexer: зачем Virtual Threads? (I/O-bound задача, чтение диска, отсутствие оверхеда OS-threads).
- [ ] **Логистика:**
  - [ ] Проверить камеру, микрофон, интернет.
  - [ ] Подготовить стакан воды, выспаться.

---
*Last updated: [Текущая дата]*
