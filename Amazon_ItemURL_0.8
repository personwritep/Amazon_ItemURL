// ==UserScript==
// @name        Amazon ItemURL
// @namespace        http://tampermonkey.net/
// @version        0.8
// @description        アマゾン商品ページのURLを短縮・リンクカードの生成
// @author        Amazon User
// @match        https://www.amazon.co.jp/*
// @icon        https://www.google.com/s2/favicons?sz=64&domain=amazon.co.jp
// @grant        none
// @updateURL        https://github.com/personwritep/Amazon_ItemURL/raw/main/Amazon_ItemURL.user.js
// @downloadURL        https://github.com/personwritep/Amazon_ItemURL/raw/main/Amazon_ItemURL.user.js
// ==/UserScript==


let panel_disp=0; // パネルの表示フラグ
let action; // Textリンク Cardリンク の選択フラグ
let rich; //  カードのリンク情報の表示量
let action_type=0; // 出力されるリンクタイプ

action=localStorage.getItem('AIURL_Link_action');
rich=localStorage.getItem('AIURL_Link_rich');
if(!action || !rich){
    action=0; // Textリンクが初期値
    localStorage.setItem('AIURL_Link_action', action); // 🔵ストレージ記入
    rich=0; // 説明文1行表示
    localStorage.setItem('AIURL_Link_rich', rich); } // 🔵ストレージ記入



let retry=0;
let interval=setInterval(wait_target, 20);
function wait_target(){
    retry++;
    if(retry>20){ // リトライ制限 20回 0.4secまで
        clearInterval(interval); }
    let target=document.body; // 監視 target
    if(target){
        clearInterval(interval);
        env(); }}


function env(){
    let help_url='https://ameblo.jp/personwritep/entry-12810297619.html';

    let help_svg=
        '<svg width="40" height="20" style="vertical-align: -6px;" '+
        'viewBox="0 0 200 200">'+
        '<path style="fill: #78909C" d="M92 14C54 19 23 44 15 82C4 135 49 '+
        '192 105 186C143 181 175 156 183 118C195 64 149 7 92 14z"></path>'+
        '<path style="fill: #fff" d="M63 69C70 67 76 64 82 61C92 58 116 58 110 '+
        '76C103 96 81 101 81 125L112 125C112 111 123 105 132 96C141 85 1'+
        '46 69 140 55C131 34 102 33 83 37C78 38 69 39 65 43C60 47 63 63 63 '+
        '69M83 143L83 169L111 169L111 143L83 143z"></path></svg>';

    let panel=
        '<div id="tr_panel">'+
        '<a href="'+ help_url + '" rel="noopener noreferrer" target="_blank">'+
        help_svg +'</a>'+
        '<div id="tr_url"></div>'+
        '<button id="tr_test" class="color_sw">Test</button>'+
        '<button id="tr_select" class="color_sw">'+
        '<span class="t1">Text</span> <span class="t2">Card</span></button>'+
        '<button id="tr_rich" class="color_sw"></button>'+
        '<button id="tr_copy" class="color_sw">Copy</button>'+
        '<button id="tr_close" class="color_sw">✖</button>'+
        '</div>'+
        '<style>#tr_panel { position: fixed; top: 0px; left: 0; z-index: 5000; '+
        'font: normal 16px/24px Meiryo; padding: 14px 20px 12px 0; '+
        'background: #fff; border: 1px solid #aaa; align-items: center; display: none; } '+
        '#tr_url { padding: 4px 15px 2px; border: 1px solid #aaa; '+
        'max-width: 80vw; word-break: break-word;} '+
        '#tr_select { width: 90px; white-space: nowrap; } '+
        '#tr_panel #tr_rich { margin-left: 3px; padding: 2px 0 0; width: 22px; } '+
        '#tr_panel .t1 { opacity: 1; font-size: 16px; } '+
        '#tr_panel .t2 { opacity: .3; font-size: 12px; } '+
        '#tr_panel.card .t1 { opacity: .3; font-size: 12px; } '+
        '#tr_panel.card .t2 { opacity: 1; font-size: 16px; } '+
        '#tr_panel .color_sw { margin-left: 15px; padding: 2px 8px 0; height: 32px; '+
        'border: 1px solid #aaa; background: linear-gradient(transparent, #c3e0ee); } '+
        '#tr_panel .color_sw:hover { background: linear-gradient(#c3e0ee, transparent); } '+
        '#tr_panel.card .color_sw { background: linear-gradient(transparent, #ffe082); } '+
        '#tr_panel.card .color_sw:hover { background: linear-gradient(#ffe082, transparent); } '+
        '</style>';

    if(!document.querySelector('#tr_panel')){
        document.body.insertAdjacentHTML('beforeend', panel); }}



let target=document.head; // 監視 target
let monitor=new MutationObserver(item_page);
monitor.observe(target, {childList: true}); // 監視開始

function item_page(){
    let nav_a=document.querySelector('#nav-logo a');
    if(nav_a){
        nav_a.style.outline="2px solid red"; }

    let nav=document.querySelector('#nav-logo');
    if(nav){
        nav.onclick=function(event){
            if(!event.ctrlKey && !event.shiftKey){
                event.preventDefault();
                tr_short(); }}}}



function tr_short(){
    let tr_panel=document.querySelector('#tr_panel');
    if(tr_panel){
        if(panel_disp==0){
            panel_disp=1;
            tr_panel.style.display='flex';
            main(); }
        else{
            panel_disp=0;
            tr_panel.style.display='none'; }}}



function main(){
    let url_input=document.querySelector('#tr_url');
    if(url_input){
        let def_url=location.href;
        let smart_url;
        let product;

        if(def_url.indexOf('www.amazon.co')==-1){ // Amazon以外
            smart_url=cut_after(def_url, '?'); }
        else{ // Amazonの場合
            if(def_url.indexOf('/b/')==-1 && def_url.indexOf('/b?')==-1 &&
               def_url.indexOf('/s/')==-1 && def_url.indexOf('/s?')==-1 &&
               cut_before(def_url, '?').indexOf('node=')==-1){
                if(def_url.indexOf('/gp/')!=-1){
                    product=cut_after(cut_before(cut_after(def_url, '?'), '/gp/'), '/ref=');
                    smart_url='https://www.amazon.co.jp'+ product; }
                else if(def_url.indexOf('/dp/')!=-1){
                    product=cut_after(cut_before(cut_after(def_url, '?'), '/dp/'), '/ref=');
                    smart_url='https://www.amazon.co.jp'+ product; }
                else{
                    smart_url=cut_after(def_url, '?'); }}
            else{
                smart_url=def_url; }}

        url_input.textContent=smart_url;

        act_limit();
        test();
        select_act();
        copy();
        close(); }



    function cut_before(row, string){ // 前方を削除
        let rs;
        if(row.indexOf(string)!=-1){
            rs=row.substring(row.indexOf(string));
            return rs; }
        else{
            return row; }}

    function cut_after(row, string){ // 以降を削除
        let rs;
        if(row.indexOf(string)!=-1){
            rs=row.substring(0, row.indexOf(string));
            return rs; }
        else{
            return row; }}



    function test(){
        let tr_test=document.querySelector('#tr_test');
        if(tr_test){
            tr_test.onclick=function(){
                if(panel_disp==1){
                    let url_input=document.querySelector('#tr_url');
                    if(url_input.textContent){
                        window.open(url_input.textContent, '_blank'); }}}}}



    function act_limit(){
        let tr_select=document.querySelector('#tr_select');
        let tr_rich=document.querySelector('#tr_rich');
        if(tr_select && tr_rich){
            if(page_check()==0){
                tr_select.style.display='none';
                tr_rich.style.display='none'; }
            else{
                tr_select.style.display='inline';
                tr_rich.style.display='inline'; }}}



    function page_check(){
        let productTitle=document.querySelector('#productTitle');
        let tmmSwatches=document.querySelector('#tmmSwatches');
        let videoTitle=document.querySelector('h1[data-automation-id="title"]');
        if(productTitle){
            if(!tmmSwatches){
                return 1; } // 通常商品
            else{
                return 2; }} // 書籍・eBook
        else if(videoTitle){
            return 3; } // Prime Video
        else{
            return 0; }} // カード作成不可



    function select_act(){
        let rich_svg=
            '<svg width="20" height="20" viewBox="0 5 150 150">'+
            '<path style="fill: #333" d="M36 55L36 66L114 66L114 55L36 55M36 9'+
            '2L36 103L114 103L114 92L36 92M36 128L36 140L114 140L114 128L36 128z">'+
            '</path></svg>';

        let unrich_svg=
            '<svg width="20" height="20" viewBox="0 5 150 150">'+
            '<path style="fill: #333" d="M36 92L36 103L114 103L114 92L36 92z">'+
            '</path></svg>';

        let tr_panel=document.querySelector('#tr_panel');
        let tr_select=document.querySelector('#tr_select');
        let tr_rich=document.querySelector('#tr_rich');
        if(tr_panel && tr_select && tr_rich){
            sel_disp();

            tr_select.onclick=function(){
                if(action==0){
                    action=1;
                    localStorage.setItem('AIURL_Link_action', action); // 🔵ストレージ記入
                    sel_disp(); }
                else{
                    action=0;
                    localStorage.setItem('AIURL_Link_action', action); // 🔵ストレージ記入
                    sel_disp(); }}

            function sel_disp(){
                if(action==1 && page_check()!=0){
                    action_type=page_check();
                    tr_rich.style.visibility='visible';
                    tr_panel.classList.add('card'); }
                else{
                    action_type=0;
                    tr_rich.style.visibility='hidden';
                    tr_panel.classList.remove('card'); }}}


        if(tr_rich){
            if(rich==0){
                tr_rich.innerHTML=unrich_svg; }
            else{
                tr_rich.innerHTML=rich_svg; }

            tr_rich.onclick=function(){
                if(rich==0){
                    rich=1;
                    localStorage.setItem('AIURL_Link_rich', rich); // 🔵ストレージ記入
                    tr_rich.innerHTML=rich_svg; }
                else{
                    rich=0;
                    localStorage.setItem('AIURL_Link_rich', rich); // 🔵ストレージ記入
                    tr_rich.innerHTML=unrich_svg; }}}

    } //select_act()



    function creat_card(type){
        let item_title;
        let item_price;
        let item_overview;
        let item_img;
        let item_img_src;

        if(type==1){ // 通常の商品
            item_title='Amazon 商品 タイトル';
            let productTitle=document.querySelector('#productTitle');
            if(productTitle){
                item_title=productTitle.textContent; }

            item_price='Amazon価格';
            let PriceDisplay=
                document.querySelector('#corePriceDisplay_desktop_feature_div .a-offscreen');
            if(PriceDisplay){
                item_price=PriceDisplay.textContent; }
            else{
                PriceDisplay=document.querySelector('#sns-base-price');
                if(PriceDisplay){
                    item_price=PriceDisplay.textContent; }}

            item_overview='商品説明';
            let productOverview=document.querySelector('#productOverview_feature_div table');
            if(productOverview){
                item_overview=productOverview.textContent; }
            else{
                productOverview=document.querySelector('#feature-bullets');
                if(productOverview){
                    item_overview=productOverview.textContent; }}

            if(item_overview.length>300){
                item_overview=item_overview.substr(0, 300); }

            let sam_selector=[
                '#main-image-container li.selected img',
                '#ebooks-img-wrapper img',
                '#imageBlockCommon img',
                '#leftCol img'];
            for(let k=0; k<sam_selector.length; k++){
                item_img=document.querySelector(sam_selector[k]);
                if(item_img){
                    item_img_src=item_img.getAttribute('src');
                    break; }}
        } // type==1


        if(type==2){ // 書籍・eBook
            item_title='Amazon 書籍 タイトル';
            let productTitle=document.querySelector('#productTitle');
            if(productTitle){
                item_title=productTitle.textContent; }

            item_price=''; // 著者・価格

            let bylineInfo_a=document.querySelector('#bylineInfo .author');
            if(bylineInfo_a){
                item_price=bylineInfo_a.textContent +'　'; }

            let PriceDisplay=document.querySelectorAll('#tmmSwatches .a-button-text');
            for(let k=0; k<PriceDisplay.length; k++){
                if(PriceDisplay[k].innerText){
                    let price_str=PriceDisplay[k].innerText;
                    if(price_str.indexOf('獲得ポイント')!=-1){
                        price_str=price_str.substring(0, price_str.indexOf('獲得ポイント')); }
                    price_str=price_str.replace(/\s￥/g, '￥');
                    item_price+=price_str; }}

            item_overview='書籍説明';
            let productOverview=document.querySelector('#bookDescription_feature_div');
            if(productOverview){
                item_overview=productOverview.textContent; }

            item_price+=item_overview;

            if(item_price.length>300){
                item_price=item_price.substr(0, 300); }
            item_overview='';

            let sam_selector=[
                '#img-canvas>img',
                '#ebooks-img-wrapper img',
                '#imageBlockCommon img',
                '#leftCol img'];
            for(let k=0; k<sam_selector.length; k++){
                item_img=document.querySelector(sam_selector[k]);
                if(item_img){
                    item_img_src=item_img.getAttribute('src');
                    break; }}
        } // type==2


        if(type==3){ // Prime Video
            item_title='Amazon Prime Video タイトル';
            let videoTitle=document.querySelector('h1[data-automation-id="title"]');
            if(videoTitle){
                item_title=videoTitle.textContent; }

            item_price='〔Prime Video〕';

            item_overview='商品説明';
            let videoOverview=document.querySelector('.e8yjMf');
            if(videoOverview){
                item_overview=videoOverview.textContent;
                if(item_overview.length>300){
                    item_overview=item_overview.substr(0, 300); }}

            item_img=document.querySelector('#main picture img');
            if(item_img){
                item_img_src=item_img.getAttribute('src'); }
        } // type==3


        if(!item_img_src){
            item_img_src=
                "https://m.media-amazon.com/images/I/01RmK+J4pJL._AC_UL150_.gif"; }


        let card_tx=
            '<div class="ogpCard_root">'+
            '<article class="ogpCard_wrap" '+
            'contenteditable="false" style="display: inline-block; max-width: 100%">'+
            '<a class="ogpCard_link" data-ogp-card-log="" href="'+ url_input.textContent +
            '" rel="noopener noreferrer" style="display: flex; justify-content: space-between; '+
            'overflow: hidden; box-sizing: border-box; width: 620px; max-width: 100%; '+
            'height: 120px; border: 1px solid #e2e2e2; border-radius: 4px; '+
            'background-color: #fff; text-decoration: none" target="_blank">'+
            '<span class="ogpCard_content" style="display: flex; flex-direction: column; '+
            'overflow: hidden; width: 100%; ';

        if(rich==0){
            card_tx+='padding:16px">'; }
        else{
            card_tx+='padding: 12px 16px 8px">'; }

        card_tx+=
            '<span class="ogpCard_title" style="-webkit-box-orient: vertical; '+
            'display: -webkit-box; -webkit-line-clamp: 2; max-height: 48px; font-size: 16px; '+
            'color:#333; text-align: left; font-weight: bold; overflow: hidden; ';

        if(rich==0){
            card_tx+='line-height: 1.4; ">'; }
        else{
            card_tx+='line-height: 1.25; flex-shrink: 0; ">'; }

        card_tx+=item_title +'</span>'+
            '<span class="ogpCard_description" style="overflow: hidden; text-overflow: ellipsis; '+
            'font-size: 13px; color: #757575; text-align: left; ';

        if(rich==0){
            card_tx+='white-space: nowrap; line-height: 1.6; margin-top: 4px;">'; }
        else{
            card_tx+='white-space: unset; line-height: 1.4; margin-top: 1px;">'; }

        card_tx+=item_price +'　'+ item_overview +'</span>'+
            '<span class="ogpCard_url" style="display: flex; align-items: center; margin-top: auto">'+
            '<span class="ogpCard_iconWrap" style="width: 20px; height: 20px; flex-shrink: 0">'+
            '<img src="https://www.google.com/s2/favicons?domain=https://www.amazon.co.jp" '+
            'style="vertical-align: 0; margin-right: 4px; min-width: 16px;"></span>'+
            '<span class="ogpCard_urlText" style="overflow: hidden; text-overflow: ellipsis; '+
            'white-space: nowrap; font-size: 13px; text-align: left; font-weight: bold; '+
            'color: rgb(34, 34, 34);">www.amazon.co.jp</span></span></span>'+
            '<span class="ogpCard_imageWrap" style="position: relative; width: 120px; '+
            'height: 120px; flex-shrink: 0">'+
            '<img alt="card image" class="ogpCard_image" '+
            'data-ogp-card-image="" height="120" loading="lazy" src="'+ item_img_src +
            '" style="position: absolute; top: 50%; left: 50%; object-fit: contain; height: 100%; '+
            'width: 100%; transform: translate(-50%,-50%)" width="120"></span></a>'+
            '</article></div>';

        return card_tx;
    } // creat_card()



    function copy(){
        let copy_text;
        let tr_copy=document.querySelector('#tr_copy');
        if(tr_copy){
            tr_copy.onclick=function(){
                if(panel_disp==1){
                    if (navigator.clipboard){ // copyToClipboardを実行
                        if(action_type==0){
                            copy_text=url_input.textContent; }
                        else{
                            copy_text=creat_card(action_type); }
                        navigator.clipboard.writeText(copy_text);

                        tr_copy.textContent='copied';
                        setTimeout(()=>{
                            tr_copy.textContent='Copy'; }, 1000); }}}}}



    function close(){
        let tr_panel=document.querySelector('#tr_panel');
        let tr_close=document.querySelector('#tr_close');
        if(tr_panel && tr_close){
            tr_close.onclick=function(){
                panel_disp=0;
                tr_panel.style.display='none'; }}}

} // main()

