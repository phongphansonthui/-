---
title: 为仓库配置议题模板
intro: 您可以自定义贡献者在仓库中打开新议题时可使用的模板。
redirect_from:
  - /github/building-a-strong-community/creating-issue-templates-for-your-repository
  - /articles/configuring-issue-templates-for-your-repository
  - /github/building-a-strong-community/configuring-issue-templates-for-your-repository
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Community
shortTitle: 配置
---

{% ifversion fpt or ghes or ghec %}

{% data reusables.repositories.default-issue-templates %}

{% endif %}

## 创建议题模板

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
3. 在“Features（功能）”部分的“Issues（议题）”下，单击 **Set up templates（设置模板）**。 ![开始模板设置按钮](/assets/images/help/repository/set-up-templates.png)
4. 使用 Add template（添加模板）下拉菜单，单击要创建的模板类型。 ![添加模板下拉菜单](/assets/images/help/repository/add-template-drop-down-menu.png)
5. 要在提交到仓库之前预览或编辑模板，请单击 **Preview and edit（预览和编辑）**。 ![预览和编辑按钮](/assets/images/help/repository/preview-and-edit-button.png)
6. 要编辑模板，请单击 {% octicon "pencil" aria-label="The edit icon" %}，然后在字段中键入以编辑其内容。 ![议题模板编辑按钮](/assets/images/help/repository/issue-template-edit-button.png)
7. 要自动设置默认的议题标题、将议题分配给对仓库有读取权限的人或者对议题模板应用标签，请在“Optional additional information（可选附加信息）”下输入这些详细信息。 还可以通过 YAML 前页格式中的 `title`、`labels` 或 `assignees` 为议题模板添加这些详细信息。 ![议题模板的其他信息](/assets/images/help/repository/additional-issue-template-info.png)
8. 完成编辑和预览模板后，请单击页面右上角的 **Propose changes（提议更改）**。 ![提议更改按钮](/assets/images/help/repository/propose-changes-button.png)
9. 输入提交消息，描述您的更改。 ![议题模板提交消息字段](/assets/images/help/repository/issue-template-commit-message-field.png)
10. 在提交消息字段的下方，决定是直接将模板提交到默认分支，还是创建新分支并打开拉取请求。 有关拉取请求的更多信息，请参阅“[关于拉取请求](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)”。 ![选择将议题模板提交到主要或打开的拉取请求](/assets/images/help/repository/issue-template-commit-to-master-or-open-pull-request.png)
11. 单击 **Commit changes（提交更改）**。 将这些更改合并到默认分支后，贡献者在仓库中打开新议题时便可使用该模板。

{% ifversion fpt or ghec %}

## 创建议题表单

{% data reusables.community.issue-forms-beta %}

通过议题表单，您可以创建具有可自定义 Web 表单字段的议题模板。 您可以通过在仓库中使用议题表单鼓励贡献者包含特定的结构化信息。 议题表单使用 {% data variables.product.prodname_dotcom %} 表单架构以 YAML 编写。 更多信息请参阅“[{% data variables.product.prodname_dotcom %} 表单架构的语法](/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-githubs-form-schema)”。 {% data reusables.actions.learn-more-about-yaml %}

要在仓库中使用议题表单，您必须创建一个新文件并将它添加到仓库中的 `.github/ISSUE_TEMPLATE` 文件夹。

下面是议题表单配置文件的示例。

{% data reusables.community.issue-forms-sample %}

下面是议题表单的呈现版本。 ![呈现的议题表单](/assets/images/help/repository/sample-issue-form.png)

1. 选择要创建议题表单的仓库。 您可以使用您有写入权限的现有仓库，或者创建一个新的仓库。 关于创建仓库的更多信息，请参阅“[创建新仓库](/articles/creating-a-new-repository)”。
2. 在您的仓库中，创建一个名为 `.github/ISSUE_TEMPLATE/FORM-NAME.yml` 的文件，用议题表单的名称替换 `FORM-NAME`。 有关在 GitHub 上创建新文件的更多信息，请参阅“[创建新文件](/github/managing-files-in-a-repository/creating-new-files)”。
3. 在新文件的正文中，键入议题表单的内容。 更多信息请参阅“[议题表单的语法](/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms)”。
4. 将文件提交到仓库的默认分支。 更多信息请参阅“[创建新文件](/github/managing-files-in-a-repository/creating-new-files)”。

{% endif %}

## 配置模板选择器

{% data reusables.repositories.issue-template-config %}

您可以通过将 `blank_issues_enabled` 设置为 `false`，鼓励贡献者使用议题模板。 如果您将 `blank_issues_enabled` 设置为 `true`，人们可以选择打开空白议题。

{% note %}

**注：** 如果您使用旧工作流程手动在 `.github` 文件夹中创建一个 `issue_template.md` 文件并在您的 *config.yml* 文件中启用空白问题。人们选择打开空白议题时将使用 `issue_template.md` 中的模板。 如果您禁用空白议题，将永远不会使用模板。

{% endnote %}

如果您愿意在 {% data variables.product.product_name %} 之外接收某些报告，您可以使用 `contact_links` 将用户引导到外部站点。

以下是 *config.yml* 文件的一个例子：

```yaml{:copy}
blank_issues_enabled: false
contact_links:
  - name: {% data variables.product.prodname_gcf %}
    url: https://github.com/orgs/community/discussions
    about: Please ask and answer questions here.
  - name: {% data variables.product.prodname_dotcom %} Security Bug Bounty
    url: https://bounty.github.com/
    about: Please report security vulnerabilities here.
```

当文件合并到仓库的默认分支时，您的配置文件将自定义模板选择器。

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.files.add-file %}
3. 在文件名字段中，键入 `.github/ISSUE_TEMPLATE/config.yml`。 ![配置文件名](/assets/images/help/repository/template-config-file-name.png)
4. 在新文件的正文中，键入配置文件的内容。 ![配置文件内容](/assets/images/help/repository/template-config-file-content.png)
{% data reusables.files.write_commit_message %}
{% data reusables.files.choose_commit_branch %}
{% data reusables.files.propose_new_file %}

## 延伸阅读

- "[关于议题和拉取请求模板](/articles/about-issue-and-pull-request-templates)"
- “[手动为仓库创建单一议题模板](/articles/manually-creating-a-single-issue-template-for-your-repository)”
