# Maintainer: Your Name <youremail@domain.com>
pkgname=antigravity-ide-bin
pkgver=1.0.0
pkgrel=1
pkgdesc="The powerful agentic AI coding assistant IDE"
arch=('x86_64')
url="https://antigravity.google"
license=('unknown')
depends=('bash' 'nss' 'alsa-lib' 'gtk3' 'libxss' 'libxtst')
options=('!strip' '!emptydirs')
# Note: Update the source filename if it differs, or use a direct download URL.
# If using a local file, place it in the same directory as this PKGBUILD.
source=("antigravity-ide.tar.gz")
sha256sums=('SKIP')

package() {
    # Find the chrome-sandbox file to locate the root of the extracted files
    local _sandbox_path=$(find "${srcdir}" -type f -name "chrome-sandbox" | head -n 1)
    if [ -z "$_sandbox_path" ]; then
        echo "Error: Could not find 'chrome-sandbox' inside the archive."
        exit 1
    fi
    local _extracted_dir=$(dirname "$_sandbox_path")

    # Create installation directories
    install -d "${pkgdir}/opt/antigravity-ide"
    install -d "${pkgdir}/usr/bin"
    install -d "${pkgdir}/usr/share/applications"

    # Copy all extracted files to the installation directory
    cp -a "${_extracted_dir}/"* "${pkgdir}/opt/antigravity-ide/"

    # Ensure the main executable has execute permissions
    chmod +x "${pkgdir}/opt/antigravity-ide/antigravity-ide"

    # Set permissions for chrome-sandbox (chown root:root is handled by makepkg/pacman)
    chmod 4755 "${pkgdir}/opt/antigravity-ide/chrome-sandbox"

    # Create symlink
    if [ -f "${pkgdir}/opt/antigravity-ide/bin/antigravity-ide" ]; then
        chmod +x "${pkgdir}/opt/antigravity-ide/bin/antigravity-ide"
        ln -sf "/opt/antigravity-ide/bin/antigravity-ide" "${pkgdir}/usr/bin/antigravity-ide"
    else
        ln -sf "/opt/antigravity-ide/antigravity-ide" "${pkgdir}/usr/bin/antigravity-ide"
    fi

    # Create desktop shortcut
    cat > "${pkgdir}/usr/share/applications/antigravity-ide.desktop" << EOF
[Desktop Entry]
Name=Antigravity IDE
Comment=The powerful agentic AI coding assistant IDE
Exec=/opt/antigravity-ide/antigravity-ide %U
Icon=/opt/antigravity-ide/resources/app/resources/linux/code.png
Type=Application
Categories=Development;IDE;
Terminal=false
StartupWMClass=antigravity-ide
EOF
    chmod 644 "${pkgdir}/usr/share/applications/antigravity-ide.desktop"
}
