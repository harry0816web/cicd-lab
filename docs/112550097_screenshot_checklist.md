# 112550097 截圖/失敗案例操作清單

## A. 產生「成功」截圖

1. 建立/切到你的作業分支（範例）
   - `git checkout -b hw/ci-112550097`
2. 確保 repo 有新增 `.github/workflows/ci_112550097.yaml`
3. push 到 GitHub
   - `git add .`
   - `git commit -m "ci: add ci_112550097 workflow"`
   - `git push -u origin hw/ci-112550097`
4. 到 GitHub → Actions → 進入 **CI 112550097**
5. 截圖：
   - Run 列表/單次 run（綠勾成功）
   - 點進 job（看到 typecheck / prettier / tests 都成功）
   - run 頁面的 Artifacts（看到 `test-report`）
   - 測試摘要（dorny/test-reporter 產生的 check / summary）

## B. 故意製造「失敗」案例（建議：TypeScript 型別錯誤，最穩）

### B1. 製造錯誤

1. 在任一 `src/**/*.ts` 製造型別錯誤（例：把字串指派給 number）
2. push 變更
3. 到 Actions 看 run 失敗（typecheck step 會紅）
4. 截圖：
   - Failed run 總覽
   - 失敗 step log（錯誤訊息要拍到）

### B2. 修正錯誤

1. 把型別錯誤修回來
2. 再 push
3. 截圖成功 run（可用同一張成功截圖，也可再拍一張）

## C. 另一種失敗（可選）

- Prettier 格式錯誤：故意把單引號改成雙引號、或破壞縮排，讓 `npm run format:check` 失敗
- 測試失敗：改壞 handler 回傳，讓 `npm test` fail
