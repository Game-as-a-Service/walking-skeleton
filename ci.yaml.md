```yaml
        name: CI workflow
        
        on:
          pull_request:
            branches: '**'
          workflow_dispatch:
        
        env:
        	# 執行 CI 時需要的環境變數
        
        jobs:
          build:
            name: Build
            runs-on: ubuntu-latest
        
            steps:
              - name: Git checkout
                uses: actions/checkout@v3
        
              - name: Cache dependencies
                id: cache
                uses: actions/cache@v3
                with:
        					# 提供 action/cache 所需要的參數，參照文件：
        
              - name: Install dependencies
                if: steps.cache.outputs.cache-hit != 'true'
                run: # ex: yarn install --frozen-lockfile
        
              - name: Build
                run: # ex: yarn build
          
          test:
            runs-on: ubuntu-latest
            needs: build
        
            steps:
              - name: Git checkout
                uses: actions/checkout@v3
        
              - name: Cache dependencies
                id: cache
                uses: actions/cache@v3
                with:
        					# 提供 actions/cache@v3 所需要的參數，參照文件：
        
              - name: Install dependencies
                if: steps.cache.outputs.cache-hit != 'true'
                run: # ex: yarn install --frozen-lockfile
                    
              - name: Test
                run: # ex: yarn test
        
          lint:
            runs-on: ubuntu-latest
            needs: build
        
            steps:
              - name: Git checkout
                uses: actions/checkout@v3
        
              - name: Cache dependencies
                id: cache
                uses: actions/cache@v3
                with:
        					# 提供 actions/cache@v3 所需要的參數，參照文件：
        
              - name: Install dependencies
                if: steps.cache.outputs.cache-hit != 'true'
                run: # ex: yarn install --frozen-lockfile
                
              - name: lint
        				run: # ex: npx eslint@7.32.0
          
        ```