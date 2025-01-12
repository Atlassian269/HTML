<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fingerprint Browser Environment Monitor</title>
</head>
<body>
    <h1>Fingerprint Browser Monitoring</h1>
    <button id="check-fingerprint">Check Fingerprint</button>
    <pre id="result"></pre>
    <script>
        document.getElementById('check-fingerprint').addEventListener('click', function() {
            (function() {
                function getScreenResolution() {
                    return window.screen.width + 'x' + window.screen.height;
                }

                function getLanguage() {
                    return navigator.language || navigator.userLanguage;
                }

                function getUserAgent() {
                    return navigator.userAgent;
                }

                function getPlugins() {
                    let plugins = [];
                    for (let i = 0; i < navigator.plugins.length; i++) {
                        plugins.push(navigator.plugins[i].name);
                    }
                    return plugins.join(', ');
                }

                function getWebGL() {
                    let canvas = document.createElement('canvas');
                    let gl = canvas.getContext('webgl') || canvas.getContext('experimental-webgl');
                    if (!gl) return null;

                    let debugInfo = gl.getExtension('WEBGL_debug_renderer_info');
                    if (debugInfo) {
                        return gl.getParameter(debugInfo.UNMASKED_RENDERER_WEBGL);
                    }
                    return null;
                }

                function getFonts() {
                    let canvas = document.createElement('canvas');
                    let ctx = canvas.getContext('2d');
                    ctx.font = '72px monospace';
                    let defaultFonts = ctx.font;

                    let fontList = [
                        'Arial', 'Courier New', 'Georgia', 'Times New Roman', 'Verdana',
                        'Tahoma', 'Comic Sans MS', 'Trebuchet MS', 'Lucida Console', 'Lucida Sans'
                    ];
                    let result = [];
                    fontList.forEach(function(font) {
                        ctx.font = '72px ' + font;
                        if (ctx.font !== defaultFonts) {
                            result.push(font);
                        }
                    });
                    return result;
                }

                function gatherFingerprintData() {
                    return {
                        screenResolution: getScreenResolution(),
                        language: getLanguage(),
                        userAgent: getUserAgent(),
                        plugins: getPlugins(),
                        webGL: getWebGL(),
                        fonts: getFonts()
                    };
                }

                let fingerprintData = gatherFingerprintData();
                document.getElementById('result').textContent = JSON.stringify(fingerprintData, null, 2);
            })();
        });
    </script>
</body>
</html>
