# walking-skeleton
## 架構
```bash
.
├── backend            
│   ├── python #language
│       ├── flask #framework
│       ├── fastapi
│   ├── java
│   ├── ... 
├── frontend

```

# Walking Skeleton 手冊

<aside>
💡 各位知道：有 Walking Skeleton 的開發基礎，和沒有 Walking Skeleton 的開發基礎相較之下差別有多大嗎！？

這可是「完全會影響到整體士氣的一項基礎建設」，我們認為是敏捷時代中最必要的技術實踐，若技術實踐不夠完整，哪來的敏捷可言呢？
（而且 Walking Skeleton 還能重複使用喔）

</aside>

## 什麼是 Walking Skeleton?

> A "walking skeleton" is an implementation of the thinnest possible slice of real functionality that we can automatically build, deploy, and test end-to-end.
> 

Walking Skeleton 是我們可以自動構建、部署和端到端測試的最短的實際功能實現。你要找一個實際的產品功能，這個功能越小越好，它陽春但真實。在完成這個功能的過程中，我們需要做到：

1. 建立一個粗略的架構，做最基礎的技術決策來建立 walking skeleton
2. 寫一個 end-to-end test 來去自動化測試這個功能
3. 建立 automatic CI/CD pipeline：
    1. Build
    2. End-To-End Test
    3. Deploy

### Walking Skeleton 四元素
<img width="50%" alt="Walking Skeleton 四元素" src="https://github.com/larry610881/walking-skeleton/assets/51017677/bbb6cdfc-4540-431c-8d86-f78b5fd5d6c7">


Automation + 四元素

- Minimal system/software architecture
- End-to-end function
- End-to-end test
- Deployment

## 為什麼需要 Walking Skeleton?

<aside>
💡 使我從繁忙的手動事務抽離，可以更專注在創造和探索。

如果沒有在 Day1 把 Automation 做好，那 Creativity 和 Discover 就會被繁忙雜務所阻礙。

</aside>

1. 即時回饋
    - Walking Skeleton 確立好之後，我們開發的每個功能都可以透過 Automation 快速地上線，團隊能夠在開發的早期階段就得到用戶或利益相關者的反饋。
    - 這有助於確定系統的基本需求、功能和用戶體驗，並快速進行修正和改進。
2. 驗證架構
    - Walking Skeleton 可以幫助團隊驗證系統的整體架構是否正確。
    - 它提供了一個機會來測試不同功能、元件之間的堆疊、溝通，以確保它們能夠正確地整合。
3. 降低風險
    - 它可以用來驗證技術選擇、測試系統可靠性和性能，並提前發現和解決可能的問題。
4. 增量式開發
    - Walking Skeleton 符合敏捷開發方法論的原則，支持增量式開發。
    - 團隊可以從 Walking Skeleton 開始，逐步擴展和添加新功能，從而實現快速交付和可持續發展。
5. 促進合作和溝通
    - Walking Skeleton 提供了一個共同的基礎，促進了開發團隊內外的合作和溝通。
    - 通過展示系統的核心組件和功能，團隊成員可以更好地理解系統的整體結構，並在此基礎上進行討論和決策。

## 如何設置 Walking Skeleton?

1. 設置 GitHub Repository
    - 請參考**成員練功手冊**的[新手任務 一 遊戲組](https://www.notion.so/Game-as-a-Service-Project-12d16d68be814ac1a61acbc20aeb5936?pvs=21)中，第二步：開遊戲串的開遊戲串教學之[二](https://www.notion.so/Game-as-a-Service-Project-12d16d68be814ac1a61acbc20aeb5936?pvs=21)之[三](https://www.notion.so/Game-as-a-Service-Project-12d16d68be814ac1a61acbc20aeb5936?pvs=21)
2. 開發一個基本功能
    - 後端：開發一個 End Point
        1. Health Check Point `GET /health` 回傳 200 
            
            
            ```
            GET /health
            ```
            
            ```
            HTTP/1.1 200 OK
            ```
            
    - 前端：開發一個首頁和子頁面
        
        首頁需包含
        
        1. Components
            - 引用一個 Components（如 Button）
                - 可以 客製化 或 使用 UI Component Library （如 Material UI）
        2. 有 Styling
            - 可使用任意的 CSS 技術，如 Tailwind、SCSS/SASS
        3. 有一個 Link 可以切到子頁面

3. 自動化 CI / CD
    
    > 建議使用 **GitHub Action (**[Yaml 語法文件](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)**)**
    > 
    
    CI
    
    - 在每次開 PR 時執行 CI 確認，可以參考文件 [Build and test](https://docs.github.com/en/actions/automating-builds-and-tests)
        - [cache](https://docs.github.com/en/actions/using-workflows/caching-dependencies-to-speed-up-workflows) (optional)
        - build (必要)
        - lint (optional)
        - test (必要)
    <img width="50%" alt="Screen Shot 2023-06-09 at 21 19 22" src="https://github.com/larry610881/walking-skeleton/assets/51017677/68ce9c95-ab09-4329-8115-f3eeb29dd60b">

    
    - Example [ci.yaml](./ci.yaml.md)
 
    
    CD
    
    - 當 CI 流程在主要分支 (例: `main`) 跑完時，我們就可以佈署到雲端主機 (例: AWS EC2)
    - 參考文件 [Deployment](https://docs.github.com/en/actions/deployment)

- 佈署資源
    - 雲端主機
    - 雲端資料庫
