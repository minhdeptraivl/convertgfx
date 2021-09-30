<h1><a id="user-content-ttf-to-gfx-automation-script" class="anchor" aria-hidden="true" href="#ttf-to-gfx-automation-script"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Chuyển đổi font TTF sang GFX</h1>
<hr></hr>
<h3><a id="user-content-installation" class="anchor" aria-hidden="true" href="#installation"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Cài đặt</h3>
<ol>
<li>Clone this repository.</li>
<li>Tải xuống <code>luvit</code> (Lua JIT Compiler, i.e. NodeJS of Lua) tại <a href="https://luvit.io/install.html" rel="nofollow">đây</a> và đặt các tệp thực thi trong thư mục vừa clone.</li>
<li>Thực thi (các) lệnh sau trong cmd:</li>
</ol>
<p><code>lit install creationix/coro-spawn</code></p>
<ol start="4">
<li>Tải xuống <code>swfmill.exe</code> CLI/CLT tại <a href="https://www.swfmill.org/" rel="nofollow">đây</a> và đặt chúng vào thư mục vừa clone ban đầu.</li>
<li>Tải xuống <code>gfxexport.exe, zlib1.dll, libtiff3.dll và jpeg62.dll</code> CLI/CLT tại <del><a href="https://sourceforge.net/projects/btek-kingfish/files/CryENGINE%20Modded/Tools/GFxExport/">đây</a> và cũng đặt chúng vào thư mục vừa clone ban đầu</li>
</ol>
<hr></hr>
<h3><a id="user-content-how-to-use" class="anchor" aria-hidden="true" href="#how-to-use"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Cách sử </h3>
<ol>
<li>Đặt file <code>.ttf</code> vào thư mục clone ban đầu.</li>
<li>Sử dụng cmd nhập lệnh sau:
<code>luvit s.lua</code></li>
<li>Bấm enter và chờ đợi file <code>.gfx</code> được tạo ra</li>
<li>Tạo thư mục <code> stream</code> và đặt file <code>.gfx</code> vào và copy thư mục <code> stream</code> vào [Cores]/[qb]/qbcore</li>
</ol>
<code>
    <pre><span class="pl-k">local</span> fontId

Citizen.<span class="pl-c1">CreateThread</span>(<span class="pl-k">function</span>()
    <span class="pl-c1">RegisterFontFile</span>(<span class="pl-s"><span class="pl-pds">'</span>out<span class="pl-pds">'</span></span>) <span class="pl-c"><span class="pl-c">--</span> tên file .gfx của bạn</span>
    fontId <span class="pl-k">=</span> <span class="pl-c1">RegisterFontId</span>(<span class="pl-s"><span class="pl-pds">'</span>Fira Sans<span class="pl-pds">'</span></span>) <span class="pl-c"><span class="pl-c">--</span> tên font </span>

    <span class="pl-k">while</span> <span class="pl-c1">true</span> <span class="pl-k">do</span>
        <span class="pl-c1">Wait</span>(<span class="pl-c1">0</span>)
        <span class="pl-c1">SetTextFont</span>(fontId)
        <span class="pl-c1">BeginTextCommandDisplayText</span>(<span class="pl-s"><span class="pl-pds">'</span>STRING<span class="pl-pds">'</span></span>)
        <span class="pl-c1">AddTextComponentString</span>(<span class="pl-s"><span class="pl-pds">'</span>Hello, world!<span class="pl-pds">'</span></span>)
        <span class="pl-c1">EndTextCommandDisplayText</span>(<span class="pl-c1">0.5</span>, <span class="pl-c1">0.5</span>)
    <span class="pl-k">end</span>
<span class="pl-k">end</span>)</pre>
</code>
