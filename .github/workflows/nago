(function () {
    const plugin = {};

    plugin.title = 'FlcksBR';
    plugin.version = '1.0';
    plugin.author = 'Ты';
    plugin.description = 'Автоматический источник видео с flcksbr.top';

    plugin.stream = async function (item) {
        const kp_id = item.id;

        if (!kp_id || isNaN(kp_id)) return;

        const url = `https://flcksbr.top/ss/${kp_id}`;

        try {
            const response = await fetch(url);
            const html = await response.text();

            const match = html.match(/<iframe[^>]+src="([^"]+)"/);
            if (!match) return;

            const iframeUrl = match[1];

            return [{
                title: 'FlcksBR',
                file: iframeUrl,
                quality: '4K',
                player: true
            }];
        } catch (e) {
            console.error('[FlcksBR] Ошибка загрузки:', e);
            return;
        }
    };

    window.lampa_plugin(plugin);
})();
