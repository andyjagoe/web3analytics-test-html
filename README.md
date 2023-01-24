# Using Analytics with HTML

This demo shows how to instrument a plain html site with [Web3 Analytics](http://web3analytics.network/) loaded from a CDN. Additional documentation for Web3 Analytics is available [here](https://web3-analytics.gitbook.io/product-docs/).

Debug is enabled so you can see the full interaction in the console of the browser inspector. Click the 'Track event', 'Track page view', or 'Track identify visitor' to see interactions in the console.

[Demo Site](https://web3analytics-test-html.netlify.app/)

## Usage

```html
    <!-- Include `analytics` from CDN -->
    <script defer src="https://unpkg.com/analytics/dist/analytics.min.js"></script>
    <script defer src="https://unpkg.com/analytics-plugin-web3analytics@0.1.7/dist/web3analytics.min.js"></script>
    <script type="text/javascript">

        window.addEventListener('load', function() {
            /* Initialize analytics */
            var Analytics = _analytics.init({
                app: 'web3analytics-html-demo',
                debug: true,
                plugins: [
                // attach web3analytics plugin
                web3analytics.default({
                    appId: 'YOUR_APP_ID',
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
