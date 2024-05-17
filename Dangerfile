# Sometimes it's a README fix, or something like that - which isn't relevant for
# including in a project's CHANGELOG for example
declared_trivial = github.pr_title.include? "#trivial"

# Make it more obvious that a PR is a work in progress and shouldn't be merged yet
warn("PR is classed as Work in Progress") if github.pr_title.include? "[WIP]"

# Warn when there is a big PR
warn("Big PR") if git.lines_of_code > 500
warn("Bitrise artifact link")

# 環境変数 BITRISE_PUBLIC_INSTALL_PAGE_URL を取得
install_page_url = ENV['BITRISE_PUBLIC_INSTALL_PAGE_URL']

# 環境変数が存在する場合にコメントを追加
if install_page_url
  message("Public install page is available: [Click here to install](#{install_page_url})")
else
  message("No public install page URL found.")
end

# Don't let testing shortcuts get into master by accident
fail("fdescribe left in tests") if `grep -r fdescribe specs/ `.length > 1
fail("fit left in tests") if `grep -r fit specs/ `.length > 1
