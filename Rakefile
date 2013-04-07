desc "Rename everything."
task :setup, :name do |t, args|

    app_name = args[:name]
    `grep -lir APP_NAME_LOWER . | xargs -I{} sed -i -e $'s/APP_NAME_LOWER/#{app_name.downcase}/g' {}`
    `grep -lir APP_NAME . | xargs -I{} sed -i -e $'s/APP_NAME/#{app_name}/g' {}`
    `rm -fr *-e`
    `rm -fr src/*-e`
    `mv src/app/entry_point.coffee src/app/#{app_name.downcase}`
end
