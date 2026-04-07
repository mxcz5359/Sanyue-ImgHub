<template>
    <div class="page-footer" v-if="!disableFooter">
        <p class="footer-text">
            © 2024-{{ thisYear }} Designed by
            <a class="footer-name" href="https://github.com/mxcz5359" target="_blank">YunMeng</a>
            for You!
            <a :href="footerLink" target="_blank">
                <font-awesome-icon icon="paper-plane" class="footer-link-icon" />
            </a>
            <br>
            <span class="record-wrap">
                备案号：
                <a href="http://beian.miit.gov.cn/" rel="noopener" target="_blank" class="record-link">
                    鲁ICP备2026009996号-2
                </a>
                <span class="police-record">
                    <img
                        alt="公安备案图标"
                        src="https://beian.mps.gov.cn/img/logo01.dd7ff50e.png"
                        class="record-icon"
                    />
                    <a href="https://beian.mps.gov.cn/#/query/webSearch?code=xxxxxxxxxxxxxxx" rel="noreferrer" target="_blank" class="record-link">
                        鲁公网安备xxxxxxxxxxxxxxx号
                    </a>
                </span>
            </span>
        </p>
    </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
    name: 'Footer',
    computed: {
        ...mapGetters(['userConfig']),
        footerLink() {
            return this.userConfig?.footerLink || 'https://github.com/MarSeventh'
        },
        thisYear() {
            return new Date().getFullYear()
        },
        disableFooter() {
            return this.userConfig?.disableFooter || false
        }
    }
}
</script>

<style scoped>
.page-footer {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100vw;
    color: var(--page-footer-text-color);
    font-size: large;
    user-select: none;
    text-align: center;
    padding: 16px 12px;
}

@media (max-width: 768px) {
    .page-footer {
        font-size: small;
    }
}

.footer-text {
    margin: 0;
    line-height: 1.8;
}

.footer-name {
    color: var(--page-footer-name-color);
    font-weight: bold;
    text-decoration: none;
    position: relative;
    transition: all 0.3s ease;
}

.footer-name::after {
    content: '';
    position: absolute;
    width: 0;
    height: 2px;
    bottom: -2px;
    left: 0;
    background-color: var(--page-footer-name-color);
    transition: width 0.3s ease-in-out;
}

.footer-name:hover::after {
    width: 100%;
}

.footer-link-icon {
    color: var(--page-footer-name-color);
    margin-left: 5px;
    transition: transform 0.3s ease-in-out;
}

.footer-link-icon:hover {
    transform: scale(1.2) rotate(-12deg);
}

.record-wrap {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
    gap: 4px;
}

.police-record {
    display: inline-flex;
    align-items: center;
    gap: 4px;
}

.record-link {
    color: #666;
    text-decoration: none;
}

.record-link:hover {
    text-decoration: underline;
}

.record-icon {
    width: 16px;
    height: 16px;
    vertical-align: middle;
}
</style>
