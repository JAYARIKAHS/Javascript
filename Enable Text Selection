(
    function (w)
    {
        // Define variables
        const doc = w.document;
        const userSelect = 'user-select';
        const initialValue = 'initial';
        const events = ['contextmenu', 'selectstart', 'select', 'mousedown', 'mouseup'];
        const selection = w.getSelection;
        const proto = selection && selection.prototype;
        const body = doc.body || doc.getElementsByTagName('body')[0];
        const html = doc.documentElement || doc.getElementsByTagName('html')[0];
        const elements = [body, html, doc];
        const prefixes = ['webkit', 'khtml', 'moz', 'ms', ''];

        // Remove events from all elements
        for (let i = 0; i < elements.length; i++)
        {
            const el = elements[i];

            for (let j = 0; j < events.length; j++)
            {
                el['on' + events[j]] = null;
            }
        }

        // Disable text selection
        if (proto && proto.removeAllRanges)
        {
            proto.removeAllRanges();
        }
        else if (doc.selection && doc.selection.clear)
        {
            doc.selection.clear();
        }

        // Disable user-select for all prefixes
        const style = html.style;
        style.cursor = '';
        style.webkitTouchCallout = initialValue;

        for (let i = 0; i < prefixes.length; i++)
        {
            style[(prefixes[i] ? '-' + prefixes[i] + '-' : '') + userSelect] = initialValue;
        }

        // Disable events for jQuery or Zepto
        const library = w.jQuery || w.Zepto;

        if (library)
        {
            library(w).off(events.join(' '));
        }
    }
)
    (this);
