desc "Rename everything."
task :setup, :name do |t, args|

    app_name = args[0]
    `sed -i 's/APP_NAME/#{app_name}/' #{File.join(__DIR__, "index.html")}`
    
end
