## Обзор проекта
Система диалогов представляет собой визуальный редактор и runtime-компоненты
для создания и управления диалогами в играх на Unity. Система поддерживает
древовидную структуру диалогов с возможностью создания ответвлений, событий и
последовательных связей.

Постарался создать простую и гибкую систему диалогов для юнити. В будущем 
буду дорабатывать проект.
В планах: Нормальное зуммирование и анимации появления панели диалога.Может
что нибудь еще добавлю

## Основные компоненты
### 1. Dialogue (ScriptableObject)
**Назначение**: Хранит данные всего диалога
- `List<DialogueNode> Nodes` - список всех узлов диалога
- `string StartNodeID` - ID стартового узла
- `GetNodeByID(string id)` - поиск узла по ID
- `GetStartNode()` - получение стартового узла
### 2. DialogueNode
**Назначение**: Представляет один узел диалога
- `string ID` - уникальный идентификатор
- `string Speaker` - имя говорящего
- `string Text` - текст диалога
- `List<DialogueOption> Options` - варианты ответов
- `Vector2 EditorPosition` - позиция в редакторе
- `string NextNodeID` - ID следующего узла (последовательная связь)
- `string OnEnterEvent` - событие при входе в узел
- `string OnExitEvent` - событие при выходе из узла
### 3. DialogueOption
**Назначение**: Вариант ответа в диалоге
- `string Text` - текст варианта
- `string TargetNodeID` - ID целевого узла
### 4. DialogueSystem (MonoBehaviour)
**Назначение**: Управление воспроизведением диалогов
- Отображение диалогового UI
- Обработка выбора вариантов ответа
- Вызов событий диалога
- Управление потоком диалога
### 5. DialogueEditor (Editor Window)
**Назначение**: Визуальный редактор диалогов
- Создание и редактирование узлов
- Установка связей между узлами
- Настройка событий и параметров
### 6. CharacterInteraction (MonoBehaviour)
**Назначение**: Пример компонента для взаимодействия
- Запуск диалога по нажатию пробела
- Интеграция с системой диалогов
### 7. DialogueEventHandler (MonoBehaviour)
**Назначение**: Обработчик событий диалога
- Подписка на события входа/выхода из узлов
- Выполнение соответствующих действий
## Установка и использование
### 1. Создание диалога
1. В меню Unity: `Assets/Create/Dialogue System/Dialogue`
2. Откройте редактор: `Window/Dialogue Editor`
3. Выберите созданный asset диалога
### 2. Работа с редактором
**Создание узлов**:
- Кнопка "New Node" в тулбаре
- Shift + ПКМ на сетке
**Создание связей**:
- Зеленые линии - связи через варианты ответов
- Синие линии - последовательные связи (NextNodeID)
- Кнопки "Connect From/To" в узле
- Shift + клик для последовательных связей
**Удаление узлов**:
- Кнопка "X" в узле
- Ctrl + ПКМ по узлу
- Клавиша Delete при выделенном узле
### 3. Настройка событий
В каждом узле можно задать:
- `OnEnterEvent` - вызывается при входе в узел
- `OnExitEvent` - вызывается при выходе из узла
События обрабатываются в `DialogueEventHandler`
### 4. Интеграция в игру
```csharp
// Получение ссылки на систему диалогов
public DialogueSystem dialogueSystem;
// Запуск диалога
dialogueSystem.StartDialogue(yourDialogueAsset);
```
Hotkeys редактора
• Shift + ПКМ - создать новый узел
• Ctrl + ПКМ - удалить узел под курсором
• Средняя кнопка мыши - панорамирование
• Delete - удалить выделенный узел
• Shift + клик при создании связи - создать последовательную связь






The dialogue system is a visual editor and runtime components for creating and managing
dialogues in Unity games. The system supports a tree-like dialogue structure with the
ability to create branches, events, and sequential connections.
## Core Components
### 1. Dialogue (ScriptableObject)
**Purpose**: Stores data for the entire dialogue
- `List<DialogueNode> Nodes` - list of all dialogue nodes
- `string StartNodeID` - ID of the starting node
- `GetNodeByID(string id)` - find node by ID
- `GetStartNode()` - get the starting node
### 2. DialogueNode
**Purpose**: Represents a single dialogue node
- `string ID` - unique identifier
- `string Speaker` - speaker's name
- `string Text` - dialogue text
- `List<DialogueOption> Options` - response options
- `Vector2 EditorPosition` - position in the editor
- `string NextNodeID` - ID of the next node (sequential connection)
- `string OnEnterEvent` - event triggered when entering the node
- `string OnExitEvent` - event triggered when exiting the node
### 3. DialogueOption
**Purpose**: Response option in dialogue
- `string Text` - option text
- `string TargetNodeID` - ID of the target node
### 4. DialogueSystem (MonoBehaviour)
**Purpose**: Manages dialogue playback
- Displays dialogue UI
- Handles option selection
- Triggers dialogue events
- Manages dialogue flow
### 5. DialogueEditor (Editor Window)
**Purpose**: Visual dialogue editor
- Create and edit nodes
- Establish connections between nodes
- Configure events and parameters
### 6. CharacterInteraction (MonoBehaviour)
**Purpose**: Example interaction component
- Starts dialogue on Space key press
- Integrates with the dialogue system
### 7. DialogueEventHandler (MonoBehaviour)
**Purpose**: Dialogue event handler
- Subscribes to node enter/exit events
- Executes corresponding actions
## Installation and Usage
### 1. Creating a Dialogue
1. In Unity menu: `Assets/Create/Dialogue System/Dialogue`
2. Open the editor: `Window/Dialogue Editor`
3. Select the created dialogue asset
### 2. Working with the Editor
**Creating Nodes**:
- "New Node" button in toolbar
- Shift + Right-click on grid
**Creating Connections**:
- Green lines - connections through response options
- Blue lines - sequential connections (NextNodeID)
- "Connect From/To" buttons in node
- Shift + click for sequential connections
**Deleting Nodes**:
- "X" button in node
- Ctrl + Right-click on node
- Delete key when node is selected
### 3. Configuring Events
In each node you can set:
- `OnEnterEvent` - triggered when entering the node
- `OnExitEvent` - triggered when exiting the node
Events are handled in `DialogueEventHandler`
### 4. Integration into Game
```csharp
// Get reference to dialogue system
public DialogueSystem dialogueSystem;
// Start dialogue
dialogueSystem.StartDialogue(yourDialogueAsset);
```
Editor Hotkeys
• Shift + Right-click - create new node
• Ctrl + Right-click - delete node under cursor
• Middle mouse button - panning
• Delete - delete selected node
• Shift + click when creating connection - create sequential connection
