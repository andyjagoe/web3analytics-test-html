# Using Analytics with HTML

## Usage

```html
    <!-- Include `analytics` from CDN -->
    <script defer src="https://unpkg.com/analytics/dist/analytics.min.js"></script>
    <script defer src="https://unpkg.com/analytics-plugin-web3analytics@0.1.6/dist/web3analytics.min.js"></script>
    <script type="text/javascript">

        window.addEventListener('load', function() {
            /* Initialize analytics */
            var Analytics = _analytics.init({
                app: 'web3analytics-html-demo',
                debug: true,
                plugins: [
                // attach web3analytics plugin
                web3analytics.default({
                    appId: '0xE6d24e69A35944FD15EF2948cA8E07067BD5d57a',
                    jsonRpcUrl: 'https://rinkeby.infura.io/v3/your_api_key'
                })
                ]
            })
            /* Fire page view */
            Analytics.page()
            
            /* Expose functions */
            window.trackEvent = function() {
                Analytics.track('buttonClicked')
            }
            window.pageView = function() {
                Analytics.page()
            }
            window.identifyVisitor = function() {
                Analytics.identify('user-123', {
                    pro: true,
                })
            }

            /*
            // Attach a listener
            Analytics.on('*', ({ payload }) => {
                console.log(`Event ${payload.type}`, payload)
            });
            */

        });
    </script>
```