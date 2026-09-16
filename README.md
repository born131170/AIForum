# Корпоративный форум техподдержки с AI-ассистентом (RAG)

Форум (топики/треды/роли/бан) + AI-поиск по вашей документации: FastAPI + React (Vite) + ChromaDB + LangChain.
AI-провайдеры: любые OpenAI-совместимые (ProxyAPI, OpenRouter и др.), NLPCloud и GigaChat (Сбер, библиотека gigachat).
Эмбеддинги на выбор: локально (fastembed, офлайн), GigaChat Embeddings, OpenAI Embeddings - переключаются в админ-панели.
Поиск гибридный: семантика + фильтр по шифру/типу документа (ABCD.XXXXXX.XXX, Изделие_ и т.п.) + ключевые слова, со сносками на источники.

## Требования
- Python 3.10+
- Node.js 18+ (рекомендуется 22)

## Быстрый старт (Windows)
    cd backend
    python -m venv venv
    venv\Scripts\activate.bat
    pip install -r requirements.txt
    cd ..\frontend
    npm install
    cd ..\backend
    uvicorn app.main:app --reload --port 8000   (терминал 1)
    cd ..\frontend
    npm run dev                                  (терминал 2)
Откройте http://localhost:5173

## Быстрый старт (Linux)
То же, но `source venv/bin/activate`; запуск: `uvicorn app.main:app --host 0.0.0.0 --port 8000` и `npm run dev -- --host`.

## Первый запуск
- Создаются SQLite-база `support.db` и векторный индекс `chroma_db/` автоматически.
- Стартовый администратор: **admin / admin123** - смените пароль после входа!
- Ключи AI-провайдеров задаются в админ-панели («Настройки AI») и хранятся в `backend/ai_config.json` (создаётся автоматически, в репозиторий не попадает).
- Документацию (PDF/DOCX/TXT) загружайте в админ-панели, раздел «Документация (RAG)» - индексация автоматическая.

## Безопасность
В репозиторий НЕ должны попадать: `ai_config.json`, `.env`, `support.db`, `uploads/`, `chroma_db/` - они уже в `.gitignore`.
