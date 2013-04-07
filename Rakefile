desc "Rename everything."
task :setup, :name do |t, args|

    app_name = args[0]
    `grep -lir APP_NAME_LOWER . | xargs -I{} sed -i -e $'s/APP_NAME_LOWER/#{app_name.downcase}/g' {}`
    `grep -lir APP_NAME . | xargs -I{} sed -i -e $'s/APP_NAME/#{app_name}/g' {}`
    `rm -fr *-e`
    `rm -fr src/*-e`
    
end
